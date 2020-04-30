---
description: Vous pouvez supprimer de la chronologie les plages de temps comprises entre le début et la fin dans l’heure locale.
seo-description: Vous pouvez supprimer de la chronologie les plages de temps comprises entre le début et la fin dans l’heure locale.
seo-title: Supprimer des plages
title: Supprimer des plages
uuid: 2f4afa0d-69e3-4929-8dbd-b553c8a64d96
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Supprimer des plages{#delete-ranges}

Vous pouvez supprimer de la chronologie les plages de temps comprises entre le début et la fin dans l’heure locale.

>[!NOTE]
>
>Si vous souhaitez uniquement supprimer certaines plages du contenu et que le mappage publicitaire doit être utilisé comme défini par le serveur d’annonces, créez une `CustomRangeMetadata` instance et spécifiez le type en tant qu’opération DELETE avec les plages personnalisées définies.

Supprimez des plages à l’aide d’une publicité de prise de décision publicitaire Adobe Primetime.

```
{   
    "properties": [],
    "stream": {
        "manifests": [
            {
                "url": "https://xyz.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
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
    "title": "VOD - DELETE TimeRange with Primetime ad decisioning Ads",
    "thumbnail": {
        "large": "https://example.com",
        "small": "https://example.com"
    },
    "type": "vod",
    "id": "vod_003"
}
```

