---
title: Objet JSON pour les marqueurs publicitaires personnalisés
description: Objet JSON pour les marqueurs publicitaires personnalisés
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Objet JSON pour les marqueurs publicitaires personnalisés {#json-object-for-custom-ad-markers}

Le bloc de code ci-dessous définit l’objet JSON &quot;details&quot; lorsque le type est des marqueurs d’annonce personnalisés.

Le MetadataNode renvoyé par IFeedItemAdapter:getStreamMetadata() contient 2 entrées :
1. une entrée avec clé de type `com.adobe.mediacore.metadata.DefaultMetadataKeys.CUSTOM_AD_MARKERS_METADATA_KEY` et valeur d’une instance de MetadataNode renvoyée par `TimeRangeCollection.toMetadata()`.
1. La seconde entrée comporte une clé de type `com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` avec la valeur de la variable *adapt-search-position* ci-dessous.

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
| adapt-search-position | true ou false, utilisé pour définir la valeur de la clé com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED dans le noeud de métadonnées. |
| périodes | Tableau d’objets JSON indiquant la période pour chaque marqueur de publicité. Chaque entrée d’objet JSON correspond à une instance de com.adobe.mediacore.utils.TimeRange. |
| time-ranges.begin | Valeur en ms indiquant l’heure de début du marqueur de publicité. |
| time-ranges.end | Valeur en ms indiquant l’heure de fin du marqueur de publicité. |

Pour plus d’informations sur le fonctionnement des marqueurs d’annonce personnalisés, reportez-vous à la documentation TVSDK .
