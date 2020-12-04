---
seo-title: Objet JSON pour les annonces Primetime
title: Objet JSON pour les annonces Primetime
uuid: acf968d2-9856-4ed6-a046-1ac17d176571
description: Le bloc de code ci-dessous définit l’objet JSON de détails lorsque la valeur de type est Publicités Primetime.
seo-description: Le bloc de code ci-dessous définit l’objet JSON de détails lorsque la valeur de type est Publicités Primetime.
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Objet JSON pour les publicités Primetime {#json-object-for-primetime-ads}

Le bloc de code ci-dessous définit l’objet JSON de détails lorsque la valeur de type est Publicités Primetime.

```
“metadata”: {
    “ad” :  {
        “type”: “Primetime ads”,
        “details”: {
            "domain": "sandbox2.auditude.com",
            "mediaid": "rom_asset_case_1",
            "zoneid": "109754",
            "targeting": [
                {
                    "key": "osmfKeyMulAdsAvail12346",
                    "value": "MulAdsAvail12346"
                }
            ]
        }
    }
}
```

| Propriété | Description |
|---|---|
| domain | Domaine publicitaire Primetime à utiliser pour les requêtes publicitaires. |
| médiaid | médiaid configuré dans les publicités Primetime pour ce contenu. |
| zoneid | Le Primetime annonce zoneid. Pour plus d’informations, consultez la documentation sur les publicités Primetime. |
| ciblage | Tableau de paires clé/valeur utilisées pour cibler des publicités spécifiques pour le contenu. |

Voir [com.adobe.mediacore.metadata.AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/metadata/AuditudeSettings.html) pour plus d’informations sur la valeur de ces attributs.