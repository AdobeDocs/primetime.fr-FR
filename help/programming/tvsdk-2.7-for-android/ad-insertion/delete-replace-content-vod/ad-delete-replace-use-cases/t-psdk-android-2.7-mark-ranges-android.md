---
description: Vous pouvez désigner des intervalles de temps dans le contenu VOD comme coupures publicitaires.
title: Marquer les plages
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---


# Marquer les plages {#mark-ranges}

Vous pouvez désigner des intervalles de temps dans le contenu VOD comme coupures publicitaires.

Le `TimeRanges` entre `begin` et `end` dans `localTime` sera marqué comme `AdBreak` dans le plan de montage chronologique. Les autres paramètres d’annonce sont ignorés.

>[!TIP]
>
>Si vous souhaitez marquer uniquement certaines plages du contenu en tant que publicités, sans insertion d’annonces dynamiques, créez une instance `CustomRangeMetadata` et spécifiez le type en tant qu’opération `MARK` avec les plages personnalisées définies.

1. Appuyez sur pour marquer les plages :

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

