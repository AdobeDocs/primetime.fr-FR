---
seo-title: Objet JSON pour les marqueurs publicitaires personnalisés
title: Objet JSON pour les marqueurs publicitaires personnalisés
uuid: 2c05d9ce-a22f-4829-bfea-9dcf0dc7cd6d
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Objet JSON pour les marqueurs publicitaires personnalisés {#json-object-for-custom-ad-markers}

Le bloc de code ci-dessous définit l’objet JSON &quot;details&quot; lorsque le type est des marqueurs publicitaires personnalisés.

Le MetadataNode renvoyé par IFeedItemAdapter:getStreamMetadata() contient 2 entrées :
1. une entrée avec la clé de type `com.adobe.mediacore.metadata.DefaultMetadataKeys.CUSTOM_AD_MARKERS_METADATA_KEY` et la valeur d’une instance de MetadataNode renvoyée par `TimeRangeCollection.toMetadata()`.
1. La deuxième entrée comporte une clé de type `com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` avec la valeur de l’attribut *modify-search-position* ci-dessous.

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
| ajuster-rechercher-position | true ou false, utilisé pour définir la valeur de la clé com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED dans le noeud MetadataNode. |
| plages horaires | Tableau d’objets JSON indiquant la période de chaque marqueur d’annonce. Chaque entrée d’objet JSON correspond à une instance de com.adobe.mediacore.utils.TimeRange. |
| time-range.begin | Valeur en ms indiquant l’heure de  du marqueur de publicité. |
| time-range.end | Valeur en ms indiquant l’heure de fin du marqueur de publicité. |

Reportez-vous à la documentation TVSDK pour plus d’informations sur le fonctionnement des marqueurs publicitaires personnalisés.
