---
description: Vous pouvez supprimer de la chronologie les plages de dates comprises entre le début et la fin dans localTime.
seo-description: Vous pouvez supprimer de la chronologie les plages de dates comprises entre le début et la fin dans localTime.
seo-title: Supprimer des plages
title: Supprimer des plages
uuid: 637829a7-efa8-4b83-9a04-ef01c043621f
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Supprimer des plages{#delete-ranges}

Vous pouvez supprimer de la chronologie les plages de dates comprises entre le début et la fin dans localTime.

>[!TIP]
>
>Pour supprimer uniquement certaines plages du contenu, créez une `CustomRangeMetadata` instance et spécifiez le type comme `DELETE` opération avec les plages personnalisées définies.

Le mappage publicitaire doit être utilisé comme défini par le serveur publicitaire.

1. Pour supprimer des plages avec une publicité Adobe Primetime pour la prise de décision publicitaire :

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
                   "type": "delete",
                   "time-range-list": [
                       {
                           "begin": 0,
                           "end": 20000
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
               },
               "ad": {
                   "targeting": [
                       {
                           "value": "MulAdsAvail12346",
                           "key": "osmfKeyMulAdsAvail12346"
                       }
                   ],
                   "domain": "sandbox2.auditude.com",
                   "mediaid": "psdk_000105",
                   "zoneid": "121781"
               }     
           }
       },   
       "title": "VOD - DELETE TimeRange with xm-replace_text Phrase Ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_003"
   },
   ```

