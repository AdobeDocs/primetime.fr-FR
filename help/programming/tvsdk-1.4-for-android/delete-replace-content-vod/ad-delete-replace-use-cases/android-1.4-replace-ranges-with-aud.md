---
description: Vous pouvez insérer des publicités dans du contenu VOD.
title: Remplacer des plages de temps par une publicité
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Remplacez les plages de temps par une publicité {#replace-time-ranges-with-an-ad}.

Vous pouvez insérer des publicités dans du contenu VOD.

Dans ce cas, `TimeRanges` entre `begin` et `end` dans `localTime` sont supprimés de la chronologie. Ils sont remplacés par `AdBreak` de `begin` en `begin+replaceDuration`. Si la durée de remplacement n&#39;existe pas en tant que paramètre, le serveur effectue la détermination sur l&#39;Adbreak renvoyé.

>[!NOTE]
>
>Vous devez toujours fournir une durée de remplacement spécifique pour les plages personnalisées. Si aucune publicité n&#39;est destinée à remplacer cette plage personnalisée, indiquez une durée de remplacement de 0.

Remplacez les plages par des annonces de prise de décision et Primetime.

```
{   
    "properties": [],
    "stream": {
        "manifests": [ {
            "url": 
              "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
            "type": "hls"
        } ],
                 
        "metadata": {
            "time-ranges": {
                "type": "replace",
                "time-range-list": [ {
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
                } ]
            },
            "ad": {
                "targeting": [ {
                    "value": "MulAdsAvail12346",
                    "key": "osmfKeyMulAdsAvail12346"
                } ],
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

