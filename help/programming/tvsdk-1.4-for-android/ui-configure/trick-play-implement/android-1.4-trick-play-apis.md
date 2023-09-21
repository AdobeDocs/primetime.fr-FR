---
description: TVSDK comprend des méthodes, des propriétés et des événements pour déterminer des taux valides, des taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au retour arrière.
title: Éléments de l’API de changement de taux
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 3%

---

# Éléments de l’API de changement de taux{#rate-change-api-elements}

TVSDK comprend des méthodes, des propriétés et des événements pour déterminer des taux valides, des taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au retour arrière.

<!--<a id="section_36576E92DE6343AEBD0BBD662502365D"></a>-->

Utilisez les éléments d’API suivants pour modifier les taux de lecture :

* `PlaybackRateEvent.getRate`
* `MediaPlayer.getLocalTime`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.getAvailablePlaybackRates` - indique des taux valides.

| Valeur de taux | Effet sur la lecture |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Passe en mode avance rapide avec le multiplicateur spécifié plus rapide que la normale (par exemple, 4 est 4 fois plus rapide que la normale). |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | Bascule vers le mode de retour arrière rapide |
| 1.0 | Passe en mode de lecture normal (appel `play` est identique à la définition de la propriété rate sur 1.0) |
| 0.0 | Pauses (appel `pause` est identique à la définition de la propriété rate sur 0,0) |
