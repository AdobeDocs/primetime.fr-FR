---
description: Vous pouvez désigner des intervalles de temps dans le contenu VOD comme coupures publicitaires.
title: Marquer des plages
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Marquer des plages{#mark-ranges}

Vous pouvez désigner des intervalles de temps dans le contenu VOD comme coupures publicitaires.

Dans ce cas, `TimeRanges` entre le `begin` et `end` in `localTime` sera marqué comme un `AdBreak` dans la chronologie. Les autres paramètres de publicité sont ignorés.

>[!NOTE]
>
>Si vous souhaitez uniquement marquer certaines plages dans le contenu en tant que publicités (sans insertion de publicités dynamique), créez un `CustomRangeMetadata` et spécifiez le type en tant qu’opération MARK avec les plages personnalisées définies.

1. Marquez des plages.

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
