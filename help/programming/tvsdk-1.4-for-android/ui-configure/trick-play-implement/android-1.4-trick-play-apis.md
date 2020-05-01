---
description: TVSDK comprend des méthodes, des propriétés et des événements permettant de déterminer les taux valides, les taux courants, la prise en charge ou non de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au rembobinage.
seo-description: TVSDK comprend des méthodes, des propriétés et des événements permettant de déterminer les taux valides, les taux courants, la prise en charge ou non de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au rembobinage.
seo-title: Eléments API de changement de taux
title: Eléments API de changement de taux
uuid: 0040d35c-f9cb-4066-9bee-828ed5541194
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Eléments API de changement de taux{#rate-change-api-elements}

TVSDK comprend des méthodes, des propriétés et des événements permettant de déterminer les taux valides, les taux courants, la prise en charge ou non de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au rembobinage.

<!--<a id="section_36576E92DE6343AEBD0BBD662502365D"></a>-->

Utilisez les éléments d’API suivants pour modifier les taux de lecture :

* `PlaybackRateEvent.getRate`
* `MediaPlayer.getLocalTime`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.getAvailablePlaybackRates` - indique des tarifs valides.

| Valeur de taux | Effet sur la lecture |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Bascule en mode avance rapide avec le multiplicateur spécifié plus rapide que la normale (par exemple, 4 fois plus rapide que la normale) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | Bascule en mode de rembobinage rapide |
| 1.0 | Bascule en mode de lecture normal (appeler `play` revient à définir la propriété rate sur 1,0) |
| 0.0 | Interruptions (l’appel `pause` est identique à la définition de la propriété rate sur 0,0) |

