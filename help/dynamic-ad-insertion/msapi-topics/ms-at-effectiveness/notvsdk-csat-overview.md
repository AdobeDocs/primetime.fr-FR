---
description: Les éditeurs peuvent créer des lecteurs vidéo compatibles HLS qui fonctionnent avec le de suivi des publicités côté client du serveur de manifeste Primetime. Les interfaces avec le serveur de manifeste pour les cas de flux en direct et de vidéo à la demande (VOD) sont légèrement différentes.
seo-description: Les éditeurs peuvent créer des lecteurs vidéo compatibles HLS qui fonctionnent avec le de suivi des publicités côté client du serveur de manifeste Primetime. Les interfaces avec le serveur de manifeste pour les cas de flux en direct et de vidéo à la demande (VOD) sont légèrement différentes.
seo-title: Présentation du suivi côté client non TVSDK
title: Présentation du suivi côté client non TVSDK
uuid: fb23be01-3327-443d-82c4-fb0993e7fec1
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Présentation du suivi côté client non TVSDK {#overview-of-non-tvsdk-client-side-tracking}

Les éditeurs peuvent créer des lecteurs vidéo compatibles HLS qui fonctionnent avec le de suivi des publicités côté client du serveur de manifeste Primetime. Les interfaces avec le serveur de manifeste pour les cas de flux en direct et de vidéo à la demande (VOD) sont légèrement différentes.

Le serveur de manifeste fournit une API permettant aux lecteurs personnalisés de demander les URL suivantes, qu’ils peuvent utiliser pour signaler les  de suivi des publicités :

* Impression publicitaire
* Quatar publicitaire
* Progression de la capsule publicitaire
* Progression de la capsule de contenu

L’API du serveur de manifeste suppose que tout lecteur vidéo qui l’utilise respecte la configuration minimale requise. Voir Configuration requise [pour le lecteur](../../msapi-topics/ms-player-req.md) vidéo pour plus d’informations.

## Flux de suivi côté client {#section_cst_flow}

![](assets/pt_ssai_notvsdk_csat_ai-workflow.png)

1. Le lecteur obtient une URL de serveur de manifeste auprès de l’éditeur.
1. Le lecteur ajoute  paramètres spécifiques à ses exigences d’insertion d’annonces publicitaires et envoie une requête HTTP GET à l’URL d’amorçage qui en résulte. L’URL d’amorçage a la syntaxe suivante :

   ```
   http{s}://{manifest-server:port}/auditude/variant/{PublisherAssetID}/{urlSafeBase64({Content URL})}.m3u8?{query parameters}
   
   For example:
   https://manifest.auditude.com/auditude/variant/
   7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/aHR0cDovL3B0ZGVtb3MuY29tL3ZpZGVvcy90b3NoZHVuZW5jcnlwdGVkL2hscy90ZXN0Mi5tM3U4.m3u8?
   u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2&__sid__=docExample02
   ```

   L’URL comprend les éléments décrits dans la section [Envoyer une commande au serveur](../../msapi-topics/ms-getting-started/ms-sending-cmd.md)de manifeste.

1. Le serveur de manifeste établit une session pour ce lecteur et génère un ID de session unique. Il crée une nouvelle URL de liste de lecture M3U8 variante, qu’il renvoie au lecteur sous forme de réponse JSON. La syntaxe JSON est la suivante :

   ```
   {
    "Master-M3U8": "https://{manifest-server:port}/auditude/variant/{PublisherAssetID}/{SessionID}/
       {urlSafeBase64(content URL)}.m3u8?u={Asset ID}&z={Zone ID}&pttrackingmode=simple&pttrackingversion=v2
       &{Any other query parameters}"
   }
   
   For example:
   https://pcor3.manifest.auditude.com/auditude/variant/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3B0ZGVtb3MuY29tL3ZpZGVvcy90b3NoZHVuZW5jcnlwdGVkL2hscy90ZXN0Mi5tM3U4.3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   ```

1. Le lecteur utilise l’URL de la réponse JSON pour demander la nouvelle liste de lecture principale de variante M3U8 au serveur de manifeste .
1. Le serveur de manifeste renvoie une nouvelle variante M3U8 contenant des URL de liste de lecture au niveau du flux avec une syntaxe similaire à celle-ci :

   ```
   http{s}://{manifest-server:port}/auditude/{live|vod}/{PublisherAssetID}/
     {rendition}/{groupID}/{urlSafeBase64(bit rate stream URL)}.m3u8?u={Ad Request Id}&z={Ad Zone Id}&{Any other query parameters}
   
   For example:
   #EXTM3U
   #EXT-X-VERSION:5
   #EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English",AUTOSELECT=YES,DEFAULT=YES,FORCED=NO,LANGUAGE="eng",URI="https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/webvtt/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvd2VidnR0L1RPUy1lbjIubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2"
   #EXT-X-STREAM-INF:BANDWIDTH=10000000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/10000/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMTAwMDAvdG9jXzEwMDAwLm0zdTg.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=1300000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/1300/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMTMwMC90b2NfMTMwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=3400000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/3400/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMzQwMC90b2NfMzQwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=2100000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/2100/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMjEwMC90b2NfMjEwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=800000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/800/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvODAwL3RvY184MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=5000000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/5000/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwMC90b2NfNTAwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=7500000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/7500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNzUwMC90b2NfNzUwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=500000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwL3RvY181MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   ```

1. Le lecteur sélectionne l’URL de manifeste au niveau du flux et du débit unique approprié pour lire le contenu assemblé par la publicité. Par exemple :

   ```
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwL3RvY181MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   ```

1. Le serveur de manifeste renvoie un manifeste au niveau du flux contenant des liens vers le contenu et les liens de segments TS publicitaires. Par exemple :

   ```
      #EXTM3U
   #EXT-X-VERSION:3
   #EXT-X-TARGETDURATION:8
   #EXT-X-PLAYLIST-TYPE:VOD
   
   #EXT-X-DISCONTINUITY
   #EXTINF:8,
   https://primetime-a.akamaihd.net/assets/repackage/production/zen/195/10516675/2ac89785ee8df17a31b2594c61f6921e-300k-00001.ts
   #EXTINF:7,
   https://primetime-a.akamaihd.net/assets/repackage/production/zen/195/10516675/2ac89785ee8df17a31b2594c61f6921e-300k-00002.ts
   
   #EXT-X-DISCONTINUITY
   #EXTINF:4,
   https://www.ptdemos.com/videos/toshdunencrypted/hls/500/toc_500.0.ts
   #EXTINF:4,
   https://www.ptdemos.com/videos/toshdunencrypted/hls/500/toc_500.4000.ts
   #EXTINF:4.833,
   https://www.ptdemos.com/videos/toshdunencrypted/hls/500/toc_500.8000.ts   
   ```

   >[!NOTE]
   >
   >Le lecteur sélectionne l’URL de la liste de lecture au niveau du flux continu pour obtenir le flux de contenu. Le serveur de manifeste récupère la liste de lecture d’origine sur le réseau de diffusion de contenu. Certains encodeurs peuvent injecter des détails supplémentaires dans l’attribut de `#EXTINF` titre, par exemple :
   >
   >
   ```
   >#EXTINF:6.006,LTC=2017-08-23T13:25:47+00:00
   >```

   Puisque le serveur de manifeste ne peut pas déduire la signification des attributs non standard pour les modifier pour la liste de lecture à assemblage publicitaire, le serveur de manifeste supprime tous les attributs supplémentaires au-delà des informations de durée dans cette balise. Pour plus d’informations, consultez l’entrée [EXTINF](https://tools.ietf.org/html/rfc8216#section-4.3.2.1) dans la spécification HLS.


1. Pour demander des informations de suivi, le lecteur ajoute le paramètre  `pttrackingposition` avec n’importe quelle valeur alphanumérique à l’URL de la liste de lecture au niveau du flux pour le débit sélectionné. Par exemple :

   ```
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwL3RvY181MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d
   &z=173475&pttrackingmode=simple&pttrackingversion=v2&pttrackingposition=1
   ```

1. Le serveur manifeste renvoie le fichier de liste de lecture rempli avec un objet [JSON](../../msapi-topics/ms-list-file-formats/notvsdk-csat-sidecar.md) ou [VMAP](../../msapi-topics/ms-list-file-formats/notvsdk-csat-vmap.md) contenant les données de suivi des publicités pour le fichier m3u8 de niveau flux actuellement demandé.

   >[!NOTE]
   >
   >Le serveur de manifeste ne génère des objets de suivi des publicités que si des publicités ont été insérées dans la liste de lecture de niveau flux actuellement demandée. Si le lecteur lit une liste de lecture qui ne contient pas de publicités insérées, le serveur de manifeste renvoie un état HTTP 201 pour la demande de liste de lecture du suivi des publicités. Si le lecteur effectue la demande de suivi des publicités pour un flux en cours de lecture, le serveur de manifeste renvoie un état HTTP 500. Par exemple, si la demande de lecture actuelle est de 500.m3u8, le serveur de manifeste renvoie un JSON|VMAP dans le 500.m3u8 pour la demande de suivi des publicités. Cependant, si le lecteur bascule ensuite sur les flux pour lire le fichier 800.m3u8, les informations de suivi des publicités dans le fichier 500.m3u8 deviennent non valides, ce qui entraîne une erreur 404.

   >[!NOTE]
   >
   >Le serveur de manifeste génère l’objet de suivi des publicités en fonction de la `pttrackingversion` valeur de l’URL d’amorçage. Si la valeur `pttrackingversion` est omise ou si elle n’est pas valide, le serveur de manifeste renseigne automatiquement les informations de suivi des publicités dans les `#EXT-X-MARKER` balises de chaque liste de lecture de niveau flux demandé. Voir [pour plus de détails](../../msapi-topics/ms-at-effectiveness/ms-api-playlists.md).

1. Le lecteur demande chaque URL de suivi des publicités pour chaque de suivi des publicités au moment approprié.

>[!NOTE]
>
>Pour les flux en direct, le lecteur doit répéter les étapes 6 à 10, car le gestionnaire de package met constamment à jour la liste de lecture pendant toute la durée du  en direct.

Au cours de la lecture de la vidéo, le lecteur doit suivre la position du curseur de lecture et l’utiliser conjointement avec les URL de suivi qu’il a reçues lors de l’insertion de publicités Primetime. Les URL de suivi sont regroupées par décalage temporel depuis le début de la lecture. Pour chaque décalage de temps, il existe une URL pour chaque système publicitaire auquel envoyer des informations de suivi. Les détails supplémentaires du format diffèrent entre la vidéo en direct et la vidéo à la demande.
