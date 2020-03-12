---
description: TVSDK gère les erreurs de plage de temps en fonction du problème spécifique, soit en fusionnant, soit en réorganisant les plages de temps mal définies.
seo-description: TVSDK gère les erreurs de plage de temps en fonction du problème spécifique, soit en fusionnant, soit en réorganisant les plages de temps mal définies.
seo-title: Gestion des erreurs de suppression et de remplacement des publicités
title: Gestion des erreurs de suppression et de remplacement des publicités
uuid: ab153591-0011-44b4-87f9-be0302c2295e
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Gestion des erreurs de suppression et de remplacement des publicités {#ad-deletion-and-replacement-error-handling}

TVSDK gère les erreurs de plage de temps en fonction du problème spécifique, soit en fusionnant, soit en réorganisant les plages de temps mal définies.

TVSDK traite les `timeRanges` erreurs en fusionnant et en réordonnant par défaut. Tout d’abord, il trie les plages de temps définies par le client en fonction de l’heure de *début* . Selon cet ordre de tri, il fusionne ensuite les plages adjacentes et les rejoint s’il existe des sous-ensembles et des intersections entre les plages.

TVSDK gère les erreurs de plage de temps comme suit :

* En panne : TVSDK réorganise les plages de temps.
* Sous-ensemble - Le kit TVSDK fusionne les sous-ensembles de la période.
* Intersection - Le kit TVSDK fusionne les plages de temps croisées.
* Conflit des plages de remplacement : TVSDK choisit la durée du remplacement à partir du premier élément apparaissant `timeRange` dans le groupe en conflit.

TVSDK gère les conflits en mode de signalisation comme suit :

* Si les plages REPLACE sont définies, TVSDK change automatiquement le mode de signalisation en CUSTOM_RANGE.
* Si des plages DELETE ou MARK sont définies et que le mode de signalisation est CUSTOM_RANGE, TVSDK supprime ou marque ces plages. Il n&#39;y a pas d&#39;insertion de publicité dans ce cas.
* Si une plage DELETE ou MARK définit une durée de remplacement, TVSDK ignore cette durée.

Lorsque le serveur ne renvoie pas de valeur valide `AdBreaks`:

* TVSDK génère et traite un `NOPTimelineOperation` pour les champs vides `AdBreak`. Aucune publicité n’est lue.

## Exemples d’erreurs de période {#time-range-error-examples}

TVSDK répond aux spécifications erronées de la plage de temps en fusionnant ou en remplaçant les plages de temps selon les besoins.

Dans l’exemple suivant, quatre plages de temps DELETE intersectées sont définies. TVSDK fusionne les quatre plages de temps en une, de sorte que la plage de suppression réelle soit comprise entre 0 et 50 s.

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

Dans l’exemple suivant, quatre plages de dates REPLACE sont définies avec des plages de dates conflictuelles. Dans ce cas, TVSDK remplace les 0 à 50 s par 25 s de publicités. Il s’agit de la première durée de remplacement dans l’ordre de tri, car il existe des conflits dans les plages suivantes.

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
