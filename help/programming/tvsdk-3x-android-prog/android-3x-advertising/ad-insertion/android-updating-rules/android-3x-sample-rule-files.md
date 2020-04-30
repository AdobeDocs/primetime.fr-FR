---
description: Dans le fichier AdobeTVSDKConfig.json, vous pouvez spécifier des règles par défaut ainsi que des règles pour des zones spécifiques.
seo-description: Dans le fichier AdobeTVSDKConfig.json, vous pouvez spécifier des règles par défaut ainsi que des règles pour des zones spécifiques.
seo-title: Exemples de règles de sélection créative
title: Exemples de règles de sélection créative
uuid: 0a079544-20c1-4e08-a7e3-7617e72da43a
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# Exemples de règles de sélection créative  {#sample-creative-selection-rules}

Dans le fichier AdobeTVSDKConfig.json, vous pouvez spécifier des règles par défaut ainsi que des règles pour des zones spécifiques.

## Exemples de règles par défaut {#section_xy4_3fx_hz}

Voici un exemple de [!DNL AdobeTVSDKConfig.json] fichier qui définit uniquement les règles par défaut :

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "type": "priority",
                    "stream": "vod",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "priority",
                    "stream": "live",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "normalize",
                    "item": "host",
                    "matches": "ew",
                    "values": [
                        "redirector.gvt1.com"
                    ],
                    "find": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "replace": "videoplayback/$1/expire//$2/signature//"
                }
            ]
        }
    }
}
```

## Exemples de règles par défaut avec des règles de zone supplémentaires {#section_ocv_3fx_hz}

Voici un exemple de [!DNL AdobeTVSDKConfig.json] fichier qui définit des règles par défaut, ainsi que des règles supplémentaires pour un identifiant de zone spécifique (dans ce cas, zone **&quot;1234&quot;**) :

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "type": "priority",
                    "stream": "vod",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "priority",
                    "stream": "live",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "normalize",
                    "item": "host",
                    "matches": "ew",
                    "values": [
                        "redirector.gvt1.com"
                    ],
                    "find": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "replace": "videoplayback/$1/expire//$2/signature//"
                }
            ],
            
<b>"1234"</b>: [
                {
                    "type": "priority",
                    "matches": "nc",
                    "item": "host",
                    "values": [
                        "my.domain.com",
                        "a.bcd.com"
                    ],
                    "priority": [
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/x-flv",
                        "video/quicktime",
                        "video/webm",
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/javascript"
                    ]
                }
            ]
        }
    }
}
```
