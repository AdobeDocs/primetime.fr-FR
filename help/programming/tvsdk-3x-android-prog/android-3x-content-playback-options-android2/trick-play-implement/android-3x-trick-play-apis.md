---
description: TVSDK inclut des méthodes, des propriétés et des  de pour déterminer les taux valides, les taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au retour arrière.
seo-description: TVSDK inclut des méthodes, des propriétés et des  de pour déterminer les taux valides, les taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au retour arrière.
seo-title: Eléments de l’API de changement de taux
title: Eléments de l’API de changement de taux
uuid: c2bcd20c-0641-4d75-802c-08098786d572
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Eléments de l’API de changement de taux {#rate-change-api-elements}

TVSDK inclut des méthodes, des propriétés et des  de pour déterminer les taux valides, les taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au retour arrière.

<!--<a id="section_E5D37C71323947E2AED8B866D9835E31"></a>-->

Utilisez les éléments d’API suivants pour modifier les taux de lecture :

* `PlaybackRateEvent.getRate`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.isTrickPlaySupported`
* `MediaPlayerItem.getAvailablePlaybackRates`, qui spécifie des taux valides.

| **Valeur de taux** | **Effet sur la lecture** |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Bascule en mode avance rapide avec le multiplicateur spécifié plus rapide que la normale (par exemple, 4 fois plus rapide que la normale) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | Bascule en mode Rembobinage rapide |
| 1.0 | Bascule en mode de lecture normal (l’appel `play` équivaut à définir la propriété rate sur 1,0) |
| 0.0 | Interrompt (l’appel `pause` équivaut à définir la propriété rate sur 0,0) |