---
description: Vous pouvez supprimer de la chronologie les plages de temps comprises entre le début et la fin dans l’heure locale.
seo-description: Vous pouvez supprimer de la chronologie les plages de temps comprises entre le début et la fin dans l’heure locale.
seo-title: Supprimer des plages
title: Supprimer des plages
uuid: 2aaea7a0-5d52-49a1-901c-f71e4b081d91
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Supprimer des plages {#delete-ranges}

Vous pouvez supprimer `TimeRanges` entre `begin` et `end` dans `localTime` la chronologie.

>[!TIP]
>
>Pour supprimer uniquement certaines plages du contenu, créez une `CustomRangeMetadata` instance et spécifiez le type comme une `DELETE` opération avec les plages personnalisées définies.

Le mappage publicitaire doit être utilisé comme défini par le serveur publicitaire.

1. Pour supprimer des plages à l’aide d’une publicité de prise de décision publicitaire Adobe Primetime, procédez comme suit :

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
