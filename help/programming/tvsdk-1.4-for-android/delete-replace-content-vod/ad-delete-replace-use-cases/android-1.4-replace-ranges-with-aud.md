---
description: Vous pouvez insérer des publicités dans du contenu VOD.
seo-description: Vous pouvez insérer des publicités dans du contenu VOD.
seo-title: Remplacer les plages de temps par une publicité
title: Remplacer les plages de temps par une publicité
uuid: 50cdcc06-7df5-414b-95d4-c684bc68dce3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Remplacer les plages de temps par une publicité{#replace-time-ranges-with-an-ad}

Vous pouvez insérer des publicités dans du contenu VOD.

Dans ce cas, `TimeRanges` entre le `begin` et `end` dans `localTime` sont supprimés du plan de montage chronologique. Ils sont remplacés par un `AdBreak` de `begin` à `begin+replaceDuration`. Si la durée de remplacement n’existe pas en tant que paramètre, le serveur effectue la détermination sur l’Adbreak renvoyé.

>[!NOTE]
>
>Vous devez toujours fournir une durée de remplacement spécifique pour les plages personnalisées. Si aucune publicité n’est destinée à remplacer cette plage personnalisée, indiquez une durée de remplacement de 0.

Remplacez les plages par des publicités Primetime et de prise de décision.

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

