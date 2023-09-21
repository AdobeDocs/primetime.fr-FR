---
description: TVSDK répond à des spécifications de période erronées en fusionnant ou en remplaçant les périodes selon les besoins.
title: Exemples d’erreurs de période
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Exemples d’erreurs de période{#time-range-error-examples}

TVSDK répond à des spécifications de période erronées en fusionnant ou en remplaçant les périodes selon les besoins.

**Période du DELETE**

Dans l’exemple suivant, quatre plages horaires de DELETE se recoupent sont définies. TVSDK fusionne les quatre périodes en une, de sorte que la plage de suppression réelle soit comprise entre 0 et 50 s.

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

**Remplacer la période**

Dans l’exemple suivant, quatre périodes de remplacement sont définies avec des périodes conflictuelles. Dans ce cas, TVSDK remplace 0-50 par 25 s de publicités. Cela correspond à la première durée de remplacement dans l’ordre de tri, car des conflits se produisent dans les plages suivantes.

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
