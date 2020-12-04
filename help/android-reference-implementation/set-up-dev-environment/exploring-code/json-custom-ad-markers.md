---
seo-title: Objet JSON pour les marqueurs publicitaires personnalisés
title: Objet JSON pour les marqueurs publicitaires personnalisés
uuid: 2c05d9ce-a22f-4829-bfea-9dcf0dc7cd6d
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Objet JSON pour les marqueurs publicitaires personnalisés {#json-object-for-custom-ad-markers}

Le bloc de code ci-dessous définit l’objet JSON &quot;détails&quot; lorsque le type est des marques publicitaires personnalisées.

Le MetadataNode renvoyé par IFeedItemAdapter:getStreamMetadata() contient 2 entrées :
1. une entrée avec la clé de type `com.adobe.mediacore.metadata.DefaultMetadataKeys.CUSTOM_AD_MARKERS_METADATA_KEY` et la valeur d&#39;une instance de MetadataNode renvoyée par `TimeRangeCollection.toMetadata()`.
1. La deuxième entrée comporte une clé de type `com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` avec la valeur de l&#39;attribut *modify-search-position* ci-dessous.

```
“metadata”: {
    “ad” :  {
        “type”: “custom ad markers”,
        “details”: {
            "adjust-seek-position": true,
            "time-ranges": [
                {
                    "begin": 5000,
                    "end":15000
                },
                {
                    "begin": 120000,
                    "end":135000
                }
            ]
        }
    }
}
```

| Propriété | Description |
|---|---|
| ajuster-rechercher-position | true ou false, utilisé pour définir la valeur de la clé com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED dans le MetadataNode. |
| plages horaires | Tableau d’objets JSON indiquant la période pour chaque marqueur d’annonce. Chaque entrée d’objet JSON correspond à une instance de com.adobe.mediacore.utils.TimeRange. |
| time-ranges.begin | Valeur en ms indiquant l’heure de début du marqueur publicitaire. |
| time-ranges.end | Valeur en ms indiquant l’heure de fin du marqueur publicitaire. |

Reportez-vous à la documentation TVSDK pour plus d’informations sur le fonctionnement des marqueurs publicitaires personnalisés.
