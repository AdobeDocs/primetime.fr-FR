---
title: Objet JSON pour les coupures publicitaires directes
description: Indique l’objet JSON lorsque la valeur de type est coupure publicitaire directe.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Objet JSON pour les coupures publicitaires directes{#json-object-for-direct-ad-breaks}

Le bloc de code suivant définit l’objet JSON des détails lorsque la valeur de type est des coupures publicitaires directes.

La variable `MetadataNode` renvoyé par `IFeedItemAdapter:getStreamMetadata()` contient une entrée de type clé `com.adobe.mediacore.metadata.DefaultMetadataKeys.JSON_METADATA_KEY` et valeur d’une représentation sous forme de chaîne de la valeur d’objet JSON détaillée ci-dessous.

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
| `time` | Indique l’heure de début de la coupure publicitaire, est mappée au champ temporel dans `com.adobe.mediacore.timeline.advertising.AdBreak`. Une valeur de 0 indique une publicité preroll. |
| `replace` | Indique la durée de remplacement de la coupure publicitaire. Met en correspondance avec la variable `replaceDuration` champ dans `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `ad-list` | Une liste des publicités à lire pendant la coupure publicitaire donnée est mappée sur la variable `List<Ad>` champ dans `com.adobe.mediacore.timeline.advertising.AdBreak`. |

Le bloc de code suivant définit l’objet JSON pour le tableau de liste d’annonces.

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
| `url` | L’URL du contenu de la publicité est mappée au champ d’URL dans `com.adobe.mediacore.timeline.advertising.Ad`. |
| `duration` | La durée de la publicité est mise en correspondance avec le champ de durée dans `com.adobe.mediacore.timeline.advertising.Ad`. |
| `tag` | Chaîne de description. |
