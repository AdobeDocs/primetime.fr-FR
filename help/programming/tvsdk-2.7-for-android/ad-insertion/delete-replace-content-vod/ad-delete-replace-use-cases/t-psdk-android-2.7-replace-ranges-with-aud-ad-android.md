---
description: Vous pouvez insérer des publicités dans du contenu VOD.
seo-description: Vous pouvez insérer des publicités dans du contenu VOD.
seo-title: Remplacer des plages de temps par une publicité
title: Remplacer des plages de temps par une publicité
uuid: 8f09560c-bca3-4662-bc58-6c9cd0892476
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Remplacez les plages de temps par une publicité {#replace-time-ranges-with-an-ad}

Vous pouvez insérer des publicités dans du contenu VOD.

Le `TimeRanges` entre `begin` et `end` dans `localTime` est supprimé du plan de montage chronologique. Ces plages sont remplacées par `AdBreak` de `begin` à `begin+replaceDuration`. Si `replacement-duration` n&#39;existe pas en tant que paramètre, le serveur effectue la détermination sur le `Adbreak` renvoyé.

>[!TIP]
>
>Vous devez toujours fournir un `replacement-duration` pour les plages personnalisées. Si aucune publicité n&#39;est destinée à remplacer cette plage personnalisée, indiquez une valeur `replacement-duration` de 0.

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

