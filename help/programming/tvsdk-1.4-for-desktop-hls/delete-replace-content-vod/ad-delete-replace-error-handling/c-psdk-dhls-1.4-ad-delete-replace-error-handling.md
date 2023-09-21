---
description: TVSDK gère les erreurs de période en fonction du problème spécifique, soit en fusionnant, soit en réorganisant les périodes mal définies.
title: Gestion des erreurs de suppression et de remplacement des publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Gestion des erreurs de suppression et de remplacement des publicités {#ad-deletion-and-replacement-error-handling}

TVSDK gère les erreurs de période en fonction du problème spécifique, soit en fusionnant, soit en réorganisant les périodes mal définies.

TVSDK traite des `timeRanges` en procédant à la fusion et à la réorganisation par défaut. Tout d’abord, elle trie les plages de temps définies par le client en fonction de la variable *begin* temps. Selon cet ordre de tri, il fusionne ensuite les plages adjacentes et les relie si elles comportent des sous-ensembles et des intersections.

TVSDK gère les erreurs de période comme suit :

* En panne : TVSDK réorganise les plages de temps.
* Sous-ensemble : TVSDK fusionne les sous-ensembles de périodes.
* Intersect : TVSDK fusionne les plages intersectes.
* Conflit Remplacer les plages : TVSDK choisit la durée de remplacement à partir du premier affichage. `timeRange` dans le groupe en conflit.

TVSDK gère les conflits en mode de signalisation comme suit :

* Si les plages de remplacement sont définies, TVSDK change automatiquement le mode de signalétique en CUSTOM_RANGE.
* Si des plages de DELETE ou des plages MARK sont définies et que le mode de signalisation est CUSTOM_RANGE, TVSDK supprime ou marque ces plages. Il n’y a pas d’insertion de publicités dans ce cas.
* Si une plage de DELETE ou une plage MARK définit une durée de remplacement, TVSDK ignore cette durée.

Lorsque le serveur ne retourne pas valide `AdBreaks`:

* TVSDK génère et traite un `NOPTimelineOperation` pour le champ vide `AdBreak`. Aucune publicité n’est lue.

## Exemples d’erreurs de période {#time-range-error-examples}

TVSDK répond à des spécifications de période erronées en fusionnant ou en remplaçant les périodes selon les besoins.

Dans l’exemple suivant, quatre plages horaires de DELETE se recoupent sont définies. TVSDK fusionne les quatre périodes en une, de sorte que la plage de suppression réelle soit comprise entre 0 et 50 s.

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

Dans l’exemple suivant, quatre périodes de remplacement sont définies avec des périodes conflictuelles. Dans ce cas, TVSDK remplace 0-50 par 25 s de publicités. Cela correspond à la première durée de remplacement dans l’ordre de tri, car des conflits se produisent dans les plages suivantes.

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
