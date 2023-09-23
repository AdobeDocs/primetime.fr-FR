---
description: Certaines publicités tierces (ou créatives) ne peuvent pas être regroupées dans le flux de contenu HTTP Live Streaming (HLS)/Dynamic Adaptive Streaming over HTTP (DASH) , car leur format vidéo est incompatible avec HLS/DASH. Adobe Primetime Ad Insertion et Browser TVSDK peuvent éventuellement tenter de recompresser (transcoder) des vidéos incompatibles dans des vidéos m3u8/mpd compatibles.
title: Recompresser (transcoder) les publicités incompatibles
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Recompresser (transcoder) les publicités incompatibles{#repackage-transcode-incompatible-ads}

Certaines publicités tierces (ou créatives) ne peuvent pas être regroupées dans le flux de contenu HTTP Live Streaming (HLS)/Dynamic Adaptive Streaming over HTTP (DASH) , car leur format vidéo est incompatible avec HLS/DASH. Adobe Primetime Ad Insertion et Browser TVSDK peuvent éventuellement tenter de recompresser (transcoder) des vidéos incompatibles dans des vidéos m3u8/mpd compatibles.

Les publicités diffusées par des tiers, tels qu’un serveur de publicités d’agence, votre partenaire d’inventaire ou un réseau publicitaire, sont souvent diffusées dans des formats incompatibles, tels que le téléchargement progressif MP4.
