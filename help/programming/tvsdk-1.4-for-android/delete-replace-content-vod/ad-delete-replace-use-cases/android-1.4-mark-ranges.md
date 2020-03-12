---
description: Vous pouvez définir des intervalles de temps dans le contenu VOD comme coupures publicitaires.
seo-description: Vous pouvez définir des intervalles de temps dans le contenu VOD comme coupures publicitaires.
seo-title: Marquer les plages
title: Marquer les plages
uuid: eb99a1c2-6c0c-40a4-bac2-98dce45acfad
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Marquer les plages{#mark-ranges}

Vous pouvez définir des intervalles de temps dans le contenu VOD comme coupures publicitaires.

Dans ce cas, `TimeRanges` entre le `begin` et `end` le sera `localTime` sera marqué comme un `AdBreak` dans la chronologie. Les autres paramètres de publicité sont ignorés.

>[!NOTE]
>
>Si vous souhaitez uniquement marquer certaines plages du contenu en tant que publicités (sans insertion dynamique d’annonces), créez une `CustomRangeMetadata` instance et spécifiez le type en tant qu’opération MARK avec les plages personnalisées définies.

1. Marquez les plages.

   ```
   {   
       "properties": [],
       "stream": {
           "manifests": [ {
               "url": "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
               "type": "hls"
           } ],
           "metadata": {
               "time-ranges": {
                   "type": "mark",
                   "adjust-seek-position" : true,   
                   "time-range-list": [ {
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
                    } ]
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

