---
description: Supprimez les plages de temps entre le début et la fin dans localTime de la chronologie.
seo-description: Supprimez les plages de temps entre le début et la fin dans localTime de la chronologie.
seo-title: Supprimer des plages avec l’annonce de prise de décision et Primetime
title: Supprimer des plages avec l’annonce de prise de décision et Primetime
uuid: efd36a2f-db61-434a-bc2a-50a866f44b33
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Supprimer des plages avec l’annonce de prise de décision et Primetime{#delete-ranges-with-primetime-ad-decisioning-ad}

Supprimez les plages de temps entre le début et la fin dans localTime de la chronologie.

Supprimez des plages avec une publicité Expression.

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
                "type": "delete",
                "time-range-list": [ {
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
    "title": "VOD - DELETE TimeRange with Adobe Primetime ad decisioningxm-replace_text Phrase Ads",
    "thumbnail": {
        "large": "https://example.com",
        "small": "https://example.com"
    },
    "type": "vod",
    "id": "vod_003"
}
```

