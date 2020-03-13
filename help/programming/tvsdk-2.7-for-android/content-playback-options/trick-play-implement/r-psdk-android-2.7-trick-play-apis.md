---
description: TVSDK inclut des méthodes, des propriétés et des  de pour déterminer les taux valides, les taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au retour arrière.
seo-description: TVSDK inclut des méthodes, des propriétés et des  de pour déterminer les taux valides, les taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au retour arrière.
seo-title: Eléments de l’API de changement de taux
title: Eléments de l’API de changement de taux
uuid: 3554bf45-9419-4740-8a0e-484fc14c7436
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

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

| Valeur de taux | Effet sur la lecture |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Bascule en mode avance rapide avec le multiplicateur spécifié plus rapide que la normale (par exemple, 4 fois plus rapide que la normale) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | Bascule en mode Rembobinage rapide |
| 1.0 | Bascule en mode de lecture normal (l’appel `play` équivaut à définir la propriété rate sur 1,0) |
| 0.0 | Interrompt (l’appel `pause` équivaut à définir la propriété rate sur 0,0) |

