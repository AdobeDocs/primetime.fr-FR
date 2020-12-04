---
description: TVSDK traite les erreurs de plage de temps en fonction du problème spécifique, soit en fusionnant, soit en réordonnant les plages de temps mal définies.
seo-description: TVSDK traite les erreurs de plage de temps en fonction du problème spécifique, soit en fusionnant, soit en réordonnant les plages de temps mal définies.
seo-title: Gestion des erreurs de suppression et de remplacement des publicités
title: Gestion des erreurs de suppression et de remplacement des publicités
uuid: ab153591-0011-44b4-87f9-be0302c2295e
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# Gestion des erreurs de suppression et de remplacement des publicités {#ad-deletion-and-replacement-error-handling}

TVSDK traite les erreurs de plage de temps en fonction du problème spécifique, soit en fusionnant, soit en réordonnant les plages de temps mal définies.

TVSDK corrige les erreurs `timeRanges` en fusionnant et réordonnant par défaut. Tout d’abord, il trie les plages de temps définies par le client selon l’*heure de début*. En fonction de cet ordre de tri, il fusionne ensuite des plages adjacentes et les joint s’il existe des sous-ensembles et des intersections entre les plages.

TVSDK traite les erreurs de plage de temps comme suit :

* En panne : TVSDK réorganise les plages de temps.
* Sous-ensemble - TVSDK fusionne les sous-ensembles de plages de temps.
* Intersect - TVSDK fusionne les plages de temps qui se croisent.
* Conflit de remplacements de plages - TVSDK choisit la durée de remplacement à partir du premier `timeRange` apparaissant dans le groupe en conflit.

TVSDK traite les conflits en mode de signalisation comme suit :

* Si les plages REPLACE sont définies, TVSDK change automatiquement le mode de signalisation en CUSTOM_RANGE.
* Si des plages de DELETE ou des plages MARK sont définies et que le mode de signalisation est CUSTOM_RANGE, TVSDK supprime ou marque ces plages. Il n&#39;y a pas d&#39;insertion publicitaire dans ce cas.
* Si une plage de DELETE ou une plage MARK définit une durée de remplacement, TVSDK ignore cette durée.

Lorsque le serveur ne renvoie pas un `AdBreaks` valide :

* TVSDK génère et traite un `NOPTimelineOperation` pour le `AdBreak` vide. Aucune publicité n’est lue.

## Exemples d&#39;erreurs de période {#time-range-error-examples}

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
