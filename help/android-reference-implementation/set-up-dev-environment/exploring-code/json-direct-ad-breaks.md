---
seo-title: Objet JSON pour les coupures publicitaires directes
title: Objet JSON pour les coupures publicitaires directes
uuid: ffb901f4-0a8b-40fe-b6ba-5ffebc324cf2
description: Détaille l’objet JSON lorsque la valeur de type est sauts publicitaires directs.
seo-description: Détaille l’objet JSON lorsque la valeur de type est sauts publicitaires directs.
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Objet JSON pour les coupures publicitaires directes{#json-object-for-direct-ad-breaks}

Le bloc de code suivant définit l’objet JSON de détails lorsque la valeur de type est sauts publicitaires directs.

Le `MetadataNode` renvoyé par `IFeedItemAdapter:getStreamMetadata()` contient une entrée avec une clé de type `com.adobe.mediacore.metadata.DefaultMetadataKeys.JSON_METADATA_KEY` et une valeur de chaîne représentant la valeur d&#39;objet JSON détaillée ci-dessous.

```
“metadata”: { 
    “ad” :  { 
        “type”: “direct ad breaks”, 
        “details”: { 
            "ad-breaks": [ 
                { 
                    "tag": "break-001", 
                    "time": 0, 
                    "replace": 0, 
                    "ad-list": [ 
                        { 
                        }, 
                        { 
                        } 
                    ] 
                }, 
                { 
                    "tag": "break-002", 
                    "time": 300000, 
                    "replace": 0, 
                    "ad-list": [ 
                        { 
                        } 
                    ] 
                } 
            ] 
        } 
    } 
} 
```

| Propriété | Description |
|---|---|
| `tag` | Chaîne qui correspond au champ de balise dans `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `time` | Indique l’heure de début de la coupure publicitaire, qui correspond au champ d’heure dans `com.adobe.mediacore.timeline.advertising.AdBreak`. La valeur 0 indique une publicité preroll. |
| `replace` | Indique la durée de remplacement de la coupure publicitaire, qui correspond au `replaceDuration` champ de `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `ad-list` | liste de publicités à lire pendant la coupure publicitaire donnée, qui correspond au `List<Ad>` champ dans `com.adobe.mediacore.timeline.advertising.AdBreak`. |

Le bloc de code suivant définit l’objet JSON pour le tableau publicités-liste.

```
"ad-list": [ 
    { 
        "url": "https://cdn.auditude.com/player/downloads/data/espn/ads/csx/prog_index.m3u8", 
        "duration": 15000, 
        "tag": "1st break - 1st ad" 
    }, 
    { 
        "url": "https://cdn.auditude.com/player/downloads/data/espn/ads/csx/prog_index.m3u8", 
        "duration": 30000, 
        "tag": "1st break - 2nd ad" 
    } 
], 
```

| Propriété | Description |
|---|---|
| `url` | L’URL vers le contenu de la publicité correspond au champ URL dans `com.adobe.mediacore.timeline.advertising.Ad`. |
| `duration` | La durée de la publicité correspond au champ de durée dans `com.adobe.mediacore.timeline.advertising.Ad`. |
| `tag` | Chaîne de description. |

