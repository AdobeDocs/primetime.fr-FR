---
title: Cas d'utilisation spéciale
description: Cas d'utilisation spéciale
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# Cas d&#39;utilisation spéciale{#special-use-cases}

TVSDK favorise les paramètres de plage personnalisée par rapport aux paramètres d’annonce standard. Par exemple, si des plages MARK sont définies, les paramètres d’insertion de la publicité sont ignorés. Si les plages REPLACE sont définies, TVSDK utilise automatiquement le mode de signalisation `CustomRanges`.

1. `ReplaceRange` sans durée de remplacement

   Si la durée de remplacement est manquante, la durée de remplacement réelle est déterminée par le serveur. Le nombre de publicités placées dans ce `AdBreak` est également déterminé par le serveur.

   ```
   {
       "properties": [],
       "stream": {
           "manifests": [ {
               "url": "https://. . ./vanilla/index.m3u8",
               "type": "hls"
           } ],
           "metadata": {
               "signaling-mode": "custom time ranges",
               "time-ranges": {
                   "type": "replace",
                   "adjust-seek-position": true,
                   "time-range-list": [{
                   "begin": 0,
                   "end": 30000
               }, {
                   "begin": 60000,
                   "end": 75000
               }, {
                   "begin": 255000,
                   "end": 300000
               } ]
               },
               "ad": {             
                   "domain": "sandbox2.auditude.com",
                   "mediaid": "psdk_000105",
                   "zoneid": "121781"
               }     
           }
       },
       "title": "Verify 30Sec Pre-Roll, 15 Sec Mid roll Ad and 
       45 second Post-Roll can be replaced in one shot.",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_001"
   }
   ```

1. Plages MARK et DELETE avec durée de remplacement

   La durée de remplacement supplémentaire est ignorée.
