---
title: API BOOTSTRAP
description: API BOOTSTRAP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---

# API BOOTSTRAP {#bootstrap-api}

L’API du Bootstrap est généralement l’URL envoyée aux API de lecture vidéo/client.  Pour les options et paramètres qui peuvent être configurés, reportez-vous à la section [Paramètres de l’API Bootstrap](#bootstrap-api-parameters).

## Envoi d’une commande au serveur de manifeste {#send-a-command-to-the-manifest-server}

1. Envoyer un `HTTP GET` demande d’une URL de bootstrap construite à l’aide du modèle suivant :

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]
    ?{query parameters}
   ```

   * **Extension de fichier** Défini. `.m3u8` si le manifeste cible est HLS, `.mpd` si les manifestes cibles se trouvent dans la balise DASH.

   * **PublisherAssetID** Obligatoire. Identifiant unique de l’éditeur pour le contenu spécifique.

   * **URL de contenu** Obligatoire. URL du fichier de contenu M3U8, codé Base64 pour être sécurisé dans l’URL du serveur de manifeste. L’URL du contenu doit pointer vers un fichier de variante M3U8, même s’il n’y a qu’un flux de débit d’un seul bit.

   * **Paramètres de requête** Il s’agit de la partie la plus variée de la requête. Ils indiquent au serveur de manifeste quel type de client effectue la demande et ce qu’il souhaite que le serveur de manifeste fasse.

   Par exemple :

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **Requêtes HTTP/HTTPS**

   Le serveur de manifeste crée des URL à l’aide du même protocole HTTP que la requête du client. Si un lecteur effectue une requête HTTP (http) non sécurisée, le serveur de manifeste renvoie des URL de manifeste et des URL de suivi Auditude avec le protocole http. Si un lecteur établit une connexion HTTP (https) sécurisée, un serveur de manifeste, il renvoie les URL de manifeste et les URL de suivi Auditude avec le protocole https.

   >[!NOTE]
   >
   >Le serveur de manifeste ne peut pas modifier le protocole (HTTP ou HTTPS) des balises de suivi tierces. Vous devez contacter le contenu et les fournisseurs d’annonces tiers pour qu’ils configurent les protocoles souhaités.  Les protocoles d’URL de segments peuvent être modifiés, cependant, par défaut, utilisez les mêmes protocoles définis dans les manifestes cibles.

## Paramètres de l’API Bootstrap {#bootstrap-api-parameters}

Les paramètres de requête indiquent au serveur de manifeste quel type de client a envoyé la demande et ce que ce client souhaite que le serveur de manifeste fasse. Certains sont obligatoires et d’autres ont des formats ou des valeurs acceptables spécifiques.
L’URL complète se compose de l’URL de base suivie d’un point d’interrogation, puis `parameterName=value` arguments séparés par des esperluettes. Par exemple : `Base URL?name1=value1&name2=value2& . . .&name n=value n`.

Le serveur de manifeste reconnaît les paramètres suivants. Toute chaîne de requête\
sont transmis au serveur de publicités.

| parameter | description | formats |
|---|---|---|
| _sid_ | Identifiant unique que le serveur de manifeste utilisera pour générer l’identifiant de session. | Obligatoire pour les DASH/HLS |
| live | Avertit l’Ad Insertion Primetime que l’élément de contenu transmis est un flux en direct.  Si ce paramètre n’est pas transmis, l’insertion de publicités Primetime effectue une requête secondaire sur l’appel de manifeste initial pour déterminer si le manifeste est actif ou vide.<br>Valeurs possibles :<br>true pour le contenu en direct<br>false pour le contenu vod<br>omit pour la détection automatique | Facultatif pour HLS.  Requis pour DASH |
| z | ID de zone de la ressource qui doit être fournie à l’Ad Insertion Primetime. Fourni par le gestionnaire de compte technique de votre Adobe. | Obligatoire pour les DASH/HLS |
| pabimode | Active [insertion de coupures publicitaires partielles](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md#partial-ad-break-support) pour les flux en direct.<br>Valeurs possibles :<br>true pour activer<br>omit to disable (désactivé par défaut) | HLS/DASH |
| ptadtimeout | Permet de limiter le temps global de résolution des publicités si les fournisseurs en aval mettent trop de temps à réagir.  Les réponses de longue durée peuvent entraîner des problèmes lors de la lecture. Cela permet à la DAI Primetime de forcer une réponse dans un délai spécifique.<br>Valeurs possibles :<br>chaîne numérique en millisecondes.<br>omit to disable (désactivé par défaut) | HLS/DASH |
| ptadwindow | Durée (en secondes) de la fenêtre de recherche en amont et de prise de décision — jusqu’à quel point l’Ad Insertion Primetime recherche des signaux publicitaires lorsqu’un utilisateur de l’enregistreur de contenu numérique rejoint la diffusion. La valeur zéro désactive la prise de décision publicitaire mid-roll dans le manifeste initial, la prise de décision ne reprenant qu’après la première mise à jour. Ce paramètre est utile pour désactiver l’insertion de publicités dans des sessions qui peuvent ne durer que quelques secondes (c’est-à-dire une inversion du canal).<br>Valeurs possibles :<br>chaîne numérique 0-1800 (1800 par défaut) | HLS uniquement |
| ptassetid | Identifiant unique du contenu affecté et géré par l’éditeur.  Requis en cas d’utilisation conjointe avec l’outil de dimensionnement d’annonce Akamai. | HLS/DASH |
| ptcdn | Liste d’un ou de plusieurs CDN pour héberger des ressources transcodées. Pour plus d’informations, voir [Diffusion et stockage](/help/primetime-ad-insertion/just-in-time-transcoding/delivery-and-storage.md).<br>Valeurs possibles :<br>akamai, level3, lnw (limelight network), comcast.<br>Par défaut, les réseaux de diffusion de contenu Ad Insertion Primetime sont utilisés. | HLS/DASH |
| ptcueformat | Format spécifié des balises pour effectuer la prise de décision publicitaire (par exemple, scte35).<br>Valeurs possibles :<br>dpisimple, dpiscte35, élémentaire<br>Pour les formats de repère personnalisés, contactez le représentant du compte technique pour connaître la valeur à utiliser pour votre cas d’utilisation. | HLS/DASH |
| ptfailover | Indique au serveur de manifeste d’identifier les flux principaux et de basculement spécifiés dans la liste de lecture principale et de les traiter comme des ensembles distincts. Cela facilite le basculement et évite les erreurs de synchronisation. (Pour les appareils Apple HLS uniquement.) Pour plus d’informations, voir [Faciliter le changement de lecteur HLS](hls-switching-to-failover.md) | HLS uniquement |
| ptmulticall | Si cette option est activée, une requête de publicité distincte est envoyée pour chaque valeur trouvée dans une ressource VOD.  Par défaut, l’Ad Insertion Primetime tente de collecter toutes les informations disponibles et les envoie au serveur d’annonces dans une seule demande. Valeurs possibles : true pour activer, <br>omit to disable (désactivé par défaut) | HLS/DASH |
| ptparallelstream | Permet aux clients disposant de lecteurs qui demandent des diffusions audio ou vidéo compressées CMAF en parallèle de s’assurer que les publicités dans les pistes audio et vidéo sont cohérentes. | HLS uniquement |
| ptprotoprotoswitch | Active les règles de réécriture de manifeste et les règles de récupération des publicités nommées, qui seront généralement configurées par votre représentant du support technique.<br>Exemple : adfetch_fw, cdn_akm | HLS/DASH |
| pttagds | Permet l’injection de balises EXT-X-DISCONTINUITY-SEQUENCE dans les en-têtes HLS. Valeurs possibles : true pour activer la désactivation (désactivée par défaut). | HLS uniquement |
| pttimeline | Chaîne contenant la chronologie souhaitée du placement et du contenu de la publicité, qui remplace les coupures publicitaires dans le flux de contenu. [Voir Format de la chronologie VOD] | HLS/DASH |
| pttoken | Active les schémas de protection des jetons d’autorisation de fragment/segment de contenu pour les CDN<br>Valeurs possibles :<br>akamai, lnw (limelight), ctl (centurylink) (la segmentation par jeton par défaut est désactivée) | HLS/DASH |
| pttrackingmode | Activez les schémas de suivi des publicités.<br>Valeurs possibles :<br>simple pour le suivi des publicités côté client<br>sstm pour le suivi des publicités côté serveur<br>simplicité pour le suivi des publicités client/serveur hybride (par défaut, aucun suivi publicitaire n’est effectué) | HLS/DASH |
| pttrackingposition | Indique au serveur de manifeste de renvoyer uniquement les informations de suivi des publicités. Ne spécifiez pas ce paramètre dans la requête de bootstrap.<br>Remarque : le serveur de manifeste ignore toutes les valeurs transmises. Cependant, si vous transmettez une chaîne nulle ou vide, le serveur manifeste renvoie le M3U8 | HLS/DASH<br>Suivi côté client |
| pttrackingversion | Définit la version de format à renvoyer.<br>Valeurs possibles :<br>v1, v2, v3 ou vmap | HLS/DASH<br>Suivi côté client |
| scteTracking | Ce paramètre indique au serveur de manifeste que le lecteur qui récupère le M3U8 a besoin que les informations de balise SCTE soient récupérées.<br>Valeurs possibles :<br>true ou false (false par défaut)<br>Remarque : Les données SCTE-35 sont renvoyées dans le fichier JSON sidecar avec la combinaison suivante de valeurs de paramètre de requête :<br>ptcueformat=turner | élémentaire | nfl | DPIScte35<br>pttrackingversion=v2<br>scteTracking=true<br> | HLS uniquement |
| vetargetmultiplicateur | Le nombre de segments à partir du point d’activation Le décalage preroll est configuré à l’aide de : ( vetargetmultiplicateur * durée de cible ) + durée de la mémoire tampon.<br>Remarque : Ce paramètre s’applique uniquement aux flux HLS en direct/linéaire.<br>Valeurs possibles :<br>valeur en virgule flottante numérique<br>(par défaut : 3.0 - identique à la spécification HLS) | HLS uniquement |
| vebufferLength | Nombre de secondes à partir du point d’activation, utilisé conjointement avec le multiplicateur de ciblage.<br>Remarque : Ce paramètre s’applique uniquement aux flux HLS en direct/linéaire.<br>Valeurs possibles :<br>valeur en virgule flottante numérique<br>(valeur par défaut : 3.0) | HLS uniquement |
