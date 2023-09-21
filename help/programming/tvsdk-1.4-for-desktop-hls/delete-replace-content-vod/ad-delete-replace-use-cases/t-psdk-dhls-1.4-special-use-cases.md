---
title: Cas d’utilisation spécifiques
description: Cas d’utilisation spécifiques
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Cas d’utilisation spécifiques{#special-use-cases}

TVSDK favorise les paramètres de plage personnalisés par rapport aux paramètres de publicité standard. Par exemple, si des plages MARK sont définies, les paramètres d’insertion de la publicité sont ignorés. Si les plages REPLACE sont définies, TVSDK utilise automatiquement la variable `CustomRanges` mode de signalétique.

1. `ReplaceRange` sans durée de remplacement

   Si la durée de remplacement est manquante, la durée réelle du remplacement est déterminée par le serveur. Le nombre de publicités qui y sont placées `AdBreak` est également déterminé par le serveur.

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
