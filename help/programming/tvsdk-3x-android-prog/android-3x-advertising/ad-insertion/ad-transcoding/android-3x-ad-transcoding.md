---
description: Certaines publicités tierces (ou créatives) ne peuvent pas être assemblées dans le flux de contenu HLS (HTTP Live Streaming), car leur format vidéo est incompatible avec HLS. L’insertion d’annonces Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles dans des vidéos compatibles M3U8.
seo-description: Certaines publicités tierces (ou créatives) ne peuvent pas être assemblées dans le flux de contenu HLS (HTTP Live Streaming), car leur format vidéo est incompatible avec HLS. L’insertion d’annonces Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles dans des vidéos compatibles M3U8.
seo-title: Réparez les publicités incompatibles à l’aide d’Adobe Creative Repackaging Service (CRS).
title: Réparez les publicités incompatibles à l’aide d’Adobe Creative Repackaging Service (CRS).
uuid: ef542d13-6d52-4429-8a1e-0af2df236f12
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Réparez les publicités incompatibles à l’aide d’Adobe Creative Repackaging Service (CRS). {#repackage-incompatible-ads-using-adobe-creative-repackaging-service-crs}

Certaines publicités tierces (ou créatives) ne peuvent pas être assemblées dans le flux de contenu HLS (HTTP Live Streaming), car leur format vidéo est incompatible avec HLS. L’insertion d’annonces Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles dans des vidéos compatibles M3U8.

Les publicités diffusées par des tiers, tels qu’un serveur d’annonces d’agence, votre partenaire d’inventaire ou un réseau publicitaire, sont souvent diffusées dans des formats incompatibles, tels que le format MP4 à téléchargement progressif.

Lorsque TVSDK rencontre pour la première fois une publicité incompatible, le lecteur ignore l’annonce et émet une demande au service de reconditionnement de la création (CRS), qui fait partie du serveur principal Primetime et d’insertion, afin de recompresser la publicité dans un format compatible. CRS tente de générer plusieurs rendus M3U8 à débit binaire de la publicité et stocke ces rendus sur le réseau de de contenu Primetime (CDN). La prochaine fois que TVSDK recevra une réponse publicitaire pointant vers cette publicité, le lecteur utilisera la version compatible HLS M3U8 du CDN.

Pour activer cette fonctionnalité CRS facultative, contactez votre représentant Adobe.

>[!NOTE]
>
>Pour les clients CRS version 3.0 (et antérieure), les modifications suivantes ont été apportées à la fois à la sécurité et aux performances : >
>* Le CS Ex 3.1 continue de s’appliquer `https:` si le contenu en cours de reconditionnement est utilisé `https:`. Cela réduit la possibilité pour certains lecteurs de présenter du contenu non sécurisé.
   >
   >
* CRS 3.1 réduit considérablement les appels réseau, améliorant ainsi le temps de démarrage de la vidéo.
>



Pour plus d’informations sur CRS, voir [Creative Packaging Service (CRS)](../../../../../dynamic-ad-insertion/creative-repackaging-service/crs-overview.md).

## Activer CRS dans les applications TVSDK {#enable-crs-in-tvsdk-applications}

Pour activer CRS dans vos applications TVSDK, vous devez définir les informations suivantes dans vos paramètres Auditude :

1. Activez CRS dans `AuditudeSettings`.

   ```
   ... 
   auditudeSettings.setCreativeRepackagingEnabled(true); 
   auditudeSettings.setCreativeRepackagingFormat("application/x-mpegURL"); 
   ```
