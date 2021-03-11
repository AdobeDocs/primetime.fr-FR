---
description: Certaines publicités (ou créatives) tierces ne peuvent pas être assemblées dans le flux de contenu HLS (HTTP Live Streaming), car leur format vidéo est incompatible avec HLS. L’insertion d’annonces Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles en vidéos compatibles M3U8.
title: Réparer des annonces incompatibles à l’aide du service de reconditionnement d’Adobe Creative Repackaging Service (CRS)
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Réparer les annonces incompatibles à l’aide du service CRS (Adobe Creative Repackaging Service) {#repackage-incompatible-ads-using-adobe-creative-repackaging-service-crs}

Certaines publicités (ou créatives) tierces ne peuvent pas être assemblées dans le flux de contenu HLS (HTTP Live Streaming), car leur format vidéo est incompatible avec HLS. L’insertion d’annonces Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles en vidéos compatibles M3U8.

Les publicités provenant de divers tiers, tels qu’un serveur d’annonces d’agence, votre partenaire de stock ou un réseau publicitaire, sont souvent diffusées dans des formats incompatibles, tels que le format MP4 de téléchargement progressif.

Lorsque TVSDK rencontre pour la première fois une publicité incompatible, le lecteur ignore la publicité et envoie une demande au service de reconditionnement de la création (CRS), qui fait partie du serveur principal Primetime et d’insertion, afin de reconditionner la publicité dans un format compatible. CRS tente de générer plusieurs rendus M3U8 à débit binaire de la publicité et stocke ces rendus sur le réseau de Diffusion de contenu Primetime (CDN). La prochaine fois que TVSDK recevra une réponse publicitaire pointant vers cette publicité, le lecteur utilisera la version compatible HLS M3U8 du CDN.

Pour activer cette fonction CRS facultative, contactez votre représentant d’Adobe.

>[!NOTE]
>
>Pour les clients CRS version 3.0 (et antérieure), les modifications suivantes, à commencer par CRS version 3.1, ont amélioré à la fois la sécurité et les performances :
>
>* CRS 3.1 continue avec `https:` si le contenu reconditionné utilise `https:`. Cela réduit la possibilité pour certains lecteurs de présenter du contenu non sécurisé.
   >
   >
* CRS 3.1 réduit considérablement les appels réseau, améliorant ainsi le temps de démarrage de la vidéo.

>



Pour plus d&#39;informations sur CRS, voir [Creative Packaging Service (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_certificate_enrollment.pdf).

## Activer CRS dans les applications TVSDK{#enable-crs-in-tvsdk-applications}

Pour activer CRS dans vos applications TVSDK, vous devez définir les informations suivantes dans vos paramètres Auditude :

1. Activez CRS dans `AuditudeSettings`.

   ```
   ... 
   auditudeSettings.setCreativeRepackagingEnabled(true); 
   auditudeSettings.setCreativeRepackagingFormat("application/x-mpegURL"); 
   ```
