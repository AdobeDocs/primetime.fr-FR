---
description: Vous pouvez insérer des publicités dans du contenu VOD.
title: Remplacement de périodes par une publicité
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Remplacement de périodes par une publicité {#replace-time-ranges-with-an-ad}

Vous pouvez insérer des publicités dans du contenu VOD.

La variable `TimeRanges` entre le `begin` et `end` in `localTime` sont supprimées de la chronologie. Ces plages sont remplacées par une `AdBreak` de `begin` to `begin+replaceDuration`. Si la variable `replacement-duration` n’existe pas en tant que paramètre, le serveur effectue la détermination sur le renvoyé `Adbreak`.

>[!TIP]
>
>Vous devez toujours fournir un `replacement-duration` pour les plages personnalisées. Si aucune publicité n’est destinée à remplacer cette plage personnalisée, indiquez un `replacement-duration` de 0.

1. Pour remplacer les plages par Primetime et les annonces de prise de décision :

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
                   "type": "replace",
                   "time-range-list": [
                       {
                           "begin": 0,
                           "end": 15000,
                           "replacement-duration": 15000
                       },
                       {
                                "begin": 69000,
                                "end": 99000,
                                "replacement-duration": 30000
                       },
                       {
                           "begin": 251000,
                           "end": 281000,
                           "replacement-duration": 30000
                       },
                       {
                           "begin": 514000,
                           "end": 544000,
                           "replacement-duration": 30000
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
       "title": "VOD - Replace TimeRange with Auditude Ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_003"
   }
   ```
