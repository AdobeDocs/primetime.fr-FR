---
description: Vous pouvez définir des intervalles de temps dans le contenu VOD comme coupures publicitaires.
seo-description: Vous pouvez définir des intervalles de temps dans le contenu VOD comme coupures publicitaires.
seo-title: Marquer les plages
title: Marquer les plages
uuid: fa6047dc-9a12-42fa-9e58-8ee3a55fa866
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Marquer les plages {#mark-ranges}

Vous pouvez définir des intervalles de temps dans le contenu VOD comme coupures publicitaires.

Le `TimeRanges` entre le `begin` et `end` le sera `localTime` sera marqué comme `AdBreak` dans le plan de montage chronologique. Les autres paramètres publicitaires sont ignorés.

>[!TIP]
>
>Si vous souhaitez marquer uniquement certaines plages du contenu en tant que publicités, sans insertion dynamique d’annonces, créez une `CustomRangeMetadata` instance et spécifiez le type `MARK` en tant qu’opération avec les plages personnalisées définies.

1. Appuyez sur Marquer les plages :

   ```
   {   
       "properties": [],
       "stream": {
           "manifests": [
               {
                   "url": "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
                   "type": "hls"
               }
           ],
   
       "metadata": {
           "time-ranges": {
                   "type": "mark",
               "adjust-seek-position" : true,   
                   "time-range-list": [
                     {
                        "begin": 0,
                        "end": 15000
                       },
                     {
                        "begin": 69000,
                        "end": 99000
                       },
                     {
                         "begin": 251000,
                         "end": 281000
                       },
                     {
                         "begin": 514000,
                         "end": 544000
                       }
                    ]
   
                 }
            }           
       },   
       "title": "VOD - MARK TimeRanges and no ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
          },
       "type": "vod",
       "id": "vod_004"
   }
   ```
