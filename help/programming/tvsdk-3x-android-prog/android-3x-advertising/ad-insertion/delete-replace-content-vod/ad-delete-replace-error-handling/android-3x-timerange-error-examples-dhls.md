---
description: TVSDK répond aux spécifications erronées de la plage de temps en fusionnant ou en remplaçant les plages de temps selon les besoins.
seo-description: TVSDK répond aux spécifications erronées de la plage de temps en fusionnant ou en remplaçant les plages de temps selon les besoins.
seo-title: Exemples d’erreurs de période
title: Exemples d’erreurs de période
uuid: 25ac5985-a844-452e-ac95-5006fdf413e6
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Exemples d’erreurs de période {#time-range-error-examples}

TVSDK répond aux spécifications erronées de la plage de temps en fusionnant ou en remplaçant les plages de temps selon les besoins.

**SUPPRIMER la période**

Dans l’exemple suivant, quatre plages de temps DELETE intersectées sont définies. TVSDK fusionne les quatre plages de temps en une, de sorte que la plage de suppression réelle soit comprise entre 0 et 50 s.

```
"time-ranges": {
    "type": "delete",
    "time-range-list": [
        {
            "begin": 10000,
            "end": 35000
        },
        {
            "begin": 20000,
            "end": 50000
        },
        {
            "begin": 0,
            "end": 30000
        },
        {
            "begin": 30000,
            "end": 40000
        }
    ]
}
```

**PLACER la période**

Dans l’exemple suivant, quatre plages de dates REPLACE sont définies avec des plages de dates conflictuelles. Dans ce cas, TVSDK remplace les 0 à 50 s par 25 s de publicités. Il s’agit de la première durée de remplacement dans l’ordre de tri, car il existe des conflits dans les plages suivantes.

```
"time-ranges": {
    "type": "replace",
    "time-range-list": [
        {
            "begin": 10000,
            "end": 35000,
            "replace-duration": 15000
        },
        {
            "begin": 20000,
            "end": 50000,
            "replace-duration": 20000
        },
        {
            "begin": 0,
            "end": 30000,
            "replace-duration": 25000
        },
        {
            "begin": 30000,
            "end": 40000,
            "replace-duration": 30000
        }
    ]
}
```
