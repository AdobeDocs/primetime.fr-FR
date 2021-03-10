---
description: Certaines publicités (ou créatives) tierces ne peuvent pas être assemblées dans le flux de contenu HTTP Live Streaming (HLS)/Dynamic Adaptive Streaming over HTTP (DASH), car leur format vidéo est incompatible avec HLS/DASH. L’insertion d’annonces Adobe Primetime et le navigateur TVSDK peuvent éventuellement tenter de recompresser (transcoder) des vidéos incompatibles dans des vidéos m3u8/mpd compatibles.
title: Réparation (transcodage) de publicités incompatibles
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Réparer (transcoder) annonces incompatibles{#repackage-transcode-incompatible-ads}

Certaines publicités (ou créatives) tierces ne peuvent pas être assemblées dans le flux de contenu HTTP Live Streaming (HLS)/Dynamic Adaptive Streaming over HTTP (DASH), car leur format vidéo est incompatible avec HLS/DASH. L’insertion d’annonces Adobe Primetime et le navigateur TVSDK peuvent éventuellement tenter de recompresser (transcoder) des vidéos incompatibles dans des vidéos m3u8/mpd compatibles.

Les publicités diffusées par divers tiers, tels qu’un serveur d’annonces d’agence, votre partenaire d’inventaire ou un réseau publicitaire, sont souvent diffusées dans des formats incompatibles, tels que MP4 à téléchargement progressif.
