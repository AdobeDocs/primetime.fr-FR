---
description: Certaines publicités tierces (ou créatives) ne peuvent pas être regroupées dans le flux de contenu HTTP Live Streaming (HLS), car leur format vidéo est incompatible avec HLS. L’insertion de publicités Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles dans des vidéos compatibles M3U8.
title: Recompressez les publicités incompatibles à l’aide du service CRS (Creative Repackaging Service) Adobe.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Recompressez les publicités incompatibles à l’aide du service CRS (Creative Repackaging Service) Adobe. {#repackage-incompatible-ads-using-adobe-creative-repackaging-service-crs}

Certaines publicités tierces (ou créatives) ne peuvent pas être regroupées dans le flux de contenu HTTP Live Streaming (HLS), car leur format vidéo est incompatible avec HLS. L’insertion de publicités Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles dans des vidéos compatibles M3U8.

Les publicités diffusées par des tiers, tels qu’un serveur de publicités d’agence, votre partenaire d’inventaire ou un réseau publicitaire, sont souvent diffusées dans des formats incompatibles, tels que le format MP4 de téléchargement progressif.

Lorsque TVSDK rencontre pour la première fois une publicité incompatible, le lecteur ignore la publicité et émet une demande au service de reconditionnement de création (CRS), qui fait partie du serveur principal d’insertion de publicités Primetime, afin de la recompresser dans un format compatible. CRS tente de générer plusieurs rendus M3U8 à débit binaire de l’annonce et stocke ces rendus sur le réseau de diffusion de contenu Primetime (CDN). La prochaine fois que TVSDK reçoit une réponse publicitaire pointant vers cette publicité, le lecteur utilise la version compatible HLS M3U8 du réseau de diffusion de contenu.

Pour activer cette fonctionnalité CRS facultative, contactez votre représentant d’Adobe.

>[!NOTE]
>
>Pour les clients CRS version 3.0 (et antérieure), les modifications suivantes, à commencer par CRS version 3.1, ont amélioré la sécurité et les performances :
>
>* CRS 3.1 continue avec `https:` si le contenu en cours de réassemblage utilise `https:`. Cela réduit la possibilité pour certains lecteurs de présenter du contenu non sécurisé.
>
>* CRS 3.1 minimise considérablement les appels réseau, améliorant ainsi le temps de démarrage de la vidéo.
>

Pour plus d’informations sur CRS, voir [Creative Packaging Service (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_certificate_enrollment.pdf).

## Activation de CRS dans les applications TVSDK{#enable-crs-in-tvsdk-applications}

Pour activer CRS dans vos applications TVSDK, vous devez définir les informations suivantes dans les paramètres de votre Auditude :

1. Activer CRS dans `AuditudeSettings`.

   ```
   ... 
   auditudeSettings.setCreativeRepackagingEnabled(true); 
   auditudeSettings.setCreativeRepackagingFormat("application/x-mpegURL"); 
   ```
