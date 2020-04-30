---
description: Vous pouvez insérer des publicités dans du contenu VOD.
seo-description: Vous pouvez insérer des publicités dans du contenu VOD.
seo-title: Remplacer des plages de temps par une publicité
title: Remplacer des plages de temps par une publicité
uuid: c1d93389-cba4-4db0-877d-dbdc5183683c
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Remplacer des plages de temps par une publicité {#replace-time-ranges-with-an-ad}

Vous pouvez insérer des publicités dans du contenu VOD.

Les `TimeRanges` valeurs comprises entre le `begin` et `end` dans `localTime` sont supprimées de la chronologie. Ces plages sont remplacées par une valeur `AdBreak` de `begin` à `begin+replaceDuration`. Si le paramètre `replacement-duration` n’existe pas, le serveur effectue la détermination sur le paramètre renvoyé `Adbreak`.

>[!TIP]
>
>Vous devez toujours fournir un champ `replacement-duration` pour les plages personnalisées. Si aucune publicité n’est destinée à remplacer cette plage personnalisée, indiquez une valeur `replacement-duration` de 0.

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
