---
description: 'null'
seo-description: 'null'
seo-title: Remplacement des plages de temps par une publicité de prise de décision publicitaire Adobe Primetime
title: Remplacement des plages de temps par une publicité de prise de décision publicitaire Adobe Primetime
uuid: 101ac42d-5ba5-4487-af95-483a6594808a
translation-type: tm+mt
source-git-commit: ''

---


# Remplacement des plages de temps par une publicité de prise de décision publicitaire Adobe Primetime{#replace-time-ranges-with-an-adobe-primetime-ad-decisioning-ad}

Supprimez `TimeRanges` entre le `begin` et `end` l&#39;entrée `localTime` de la chronologie. Remplacez-le par un AdBreak de `begin` à `begin+replaceDuration`.

Remplacez les plages par des annonces de prise de décision et Primetime.

```
{   
    "properties": [],
    "stream": {
        "manifests": [ {
            "url": "https://. . ./cloudfront_vod_hls_tos_30fps.m3u8",
            "type": "hls"
        } ],
        "metadata": {
            "time-ranges": {
                "type": "replace",
                "time-range-list": [ {
                    "begin": 0,
                    "end": 15000,
                    "replace-duration": 15000
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

