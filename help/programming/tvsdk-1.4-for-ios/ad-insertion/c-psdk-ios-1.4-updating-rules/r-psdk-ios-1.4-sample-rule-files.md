---
description: Dans AdobeTVSDKConfig.json, vous pouvez spécifier des règles par défaut ainsi que des règles pour des zones spécifiques.
seo-description: Dans AdobeTVSDKConfig.json, vous pouvez spécifier des règles par défaut ainsi que des règles pour des zones spécifiques.
seo-title: Exemples de règles de sélection créative
title: Exemples de règles de sélection créative
uuid: 1d63e26c-6fe0-4643-a568-f1c34cf46c53
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Exemples de règles de sélection créative{#sample-creative-selection-rules}

Dans AdobeTVSDKConfig.json, vous pouvez spécifier des règles par défaut ainsi que des règles pour des zones spécifiques.

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

