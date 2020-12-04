---
description: TVSDK répond à des spécifications de plage de temps erronées en fusionnant ou en remplaçant les plages de temps selon les besoins.
seo-description: TVSDK répond à des spécifications de plage de temps erronées en fusionnant ou en remplaçant les plages de temps selon les besoins.
seo-title: Exemples d’erreurs de période
title: Exemples d’erreurs de période
uuid: 327b38dc-6aa3-49a7-b5e7-c343b704c5c3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Exemples d’erreurs de période{#time-range-error-examples}

TVSDK répond à des spécifications de plage de temps erronées en fusionnant ou en remplaçant les plages de temps selon les besoins.

Dans l’exemple suivant, quatre plages de temps DELETE croisées sont définies. TVSDK fusionne les quatre plages de temps en une, de sorte que la plage de suppression réelle se situe entre 0 et 50 s.

```
"time-ranges": {
    "type": "delete",
    "time-range-list": [ {
        "begin": 10000,
        "end": 35000
    }, {
        "begin": 20000,
        "end": 50000
    }, {
        "begin": 0,
        "end": 30000
    }, {
        "begin": 30000,
        "end": 40000
    } ]
}
```

Dans l&#39;exemple suivant, quatre plages de temps REPLACE sont définies avec des plages de temps conflictuelles. Dans ce cas, TVSDK remplace 0-50 par 25 annonces. Elle correspond à la première durée de remplacement dans l’ordre de tri, car il y a des conflits dans les plages suivantes.

```
"time-ranges": {
    "type": "replace",
    "time-range-list": [ {
        "begin": 10000,
        "end": 35000,
        "replace-duration": 15000
    }, {
        "begin": 20000,
        "end": 50000,
        "replace-duration": 20000
    }, {
        "begin": 0,
        "end": 30000,
        "replace-duration": 25000
    }, {
        "begin": 30000,
        "end": 40000,
        "replace-duration": 30000
    } ]
}
```

