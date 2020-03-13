---
description: TVSDK gère les erreurs de plage de temps en fonction du problème spécifique, soit en fusionnant, soit en réorganisant les plages de temps mal définies.
seo-description: TVSDK gère les erreurs de plage de temps en fonction du problème spécifique, soit en fusionnant, soit en réorganisant les plages de temps mal définies.
seo-title: Gestion des erreurs de suppression et de remplacement des publicités
title: Gestion des erreurs de suppression et de remplacement des publicités
uuid: e2e06f13-9813-4d86-b6fe-3d09f3bdb100
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Gestion des erreurs de suppression et de remplacement des publicités{#ad-deletion-and-replacement-error-handling}

TVSDK gère les erreurs de plage de temps en fonction du problème spécifique, soit en fusionnant, soit en réorganisant les plages de temps mal définies.

TVSDK traite les `timeRanges` erreurs en fusionnant et en réordonnant par défaut. Tout d’abord, il trie les plages de temps définies par le client en fonction de l’heure de *début* . Selon cet ordre de tri, il fusionne ensuite les plages adjacentes et les rejoint s’il existe des sous-ensembles et des intersections entre les plages.

TVSDK gère les erreurs de plage de temps comme suit :

* En panne : TVSDK réorganise les plages de temps.
* Sous-ensemble - Le kit TVSDK fusionne les sous-ensembles de la période.
* Intersection - Le kit TVSDK fusionne les plages de temps croisées.
* Conflit des plages de remplacement : TVSDK choisit la durée du remplacement à partir du premier élément apparaissant `timeRange` dans le groupe en conflit.

TVSDK gère les conflits en mode de signalisation avec les métadonnées publicitaires comme suit :

* Si le mode de signalisation de la publicité est en conflit avec les métadonnées de plage de temps, les métadonnées de plage de temps ont toujours la priorité. Par exemple, si le mode de signalisation de la publicité est défini comme carte du serveur ou indices de manifeste et qu’il existe également des plages de temps MARK dans les métadonnées de la publicité, le comportement obtenu est que les plages sont marquées et qu’aucune publicité n’est insérée.
* Dans le cas des plages REPLACE, si le mode de signalisation est défini comme carte serveur ou comme indices manifestes, les plages sont remplacées comme spécifié dans les plages REPLACE et il n’y a aucune insertion publicitaire par le biais du mappage serveur ou des indices manifestes. Voir Mode [de signalisation](../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-signaling-mode.md)publicitaire.

Lorsque le serveur ne renvoie pas de valeur valide `AdBreaks`:

* TVSDK génère et traite un `NOPTimelineOperation` pour les champs vides `AdBreak`. Aucune publicité n’est lue.

Pour les périodes avec les flux en direct :

* Bien que cette fonction de suppression/remplacement de publicités C3 soit destinée à être prise en charge uniquement pour VOD, les plages de temps sont également traitées pour les flux en direct, si elles sont spécifiées dans les métadonnées de la publicité.

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
