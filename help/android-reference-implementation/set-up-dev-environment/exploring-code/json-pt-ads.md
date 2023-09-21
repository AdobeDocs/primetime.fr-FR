---
title: Objet JSON pour les publicités Primetime
description: Le bloc de code ci-dessous définit l’objet JSON de détails lorsque la valeur de type est Publicités Primetime.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '120'
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
| domain | Domaine des publicités Primetime à utiliser pour les requêtes de publicité. |
| mediaid | Le média qui a été configuré dans les publicités Primetime pour ce contenu. |
| zoneid | Zoneid des publicités Primetime. Pour plus d’informations, consultez la documentation sur les publicités Primetime . |
| ciblage | Tableau de paires clé/valeur utilisées pour cibler des publicités spécifiques pour le contenu. |

Voir [com.adobe.mediacore.metadata.AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/metadata/AuditudeSettings.html) pour plus d’informations sur la valeur de ces attributs.
