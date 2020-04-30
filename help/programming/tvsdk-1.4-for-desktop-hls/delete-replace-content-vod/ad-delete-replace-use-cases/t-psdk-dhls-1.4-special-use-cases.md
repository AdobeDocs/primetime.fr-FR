---
description: 'null'
seo-description: 'null'
seo-title: Cas d'utilisation spéciale
title: Cas d'utilisation spéciale
uuid: 066bc256-4fdf-4083-b23e-0a916b3b532f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Cas d&#39;utilisation spéciale{#special-use-cases}

TVSDK favorise les paramètres de plage personnalisée par rapport aux paramètres d’annonce standard. Par exemple, si des plages MARK sont définies, les paramètres d’insertion de la publicité sont ignorés. Si les plages REPLACE sont définies, TVSDK utilise automatiquement le mode `CustomRanges` de signalisation.

1. `ReplaceRange` sans durée de remplacement

   Si la durée de remplacement est manquante, la durée de remplacement réelle est déterminée par le serveur. Le nombre de publicités placées dans cette liste `AdBreak` est également déterminé par le serveur.

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

1. Marquer et SUPPRIMER les plages avec la durée de remplacement

   La durée de remplacement supplémentaire est ignorée.
