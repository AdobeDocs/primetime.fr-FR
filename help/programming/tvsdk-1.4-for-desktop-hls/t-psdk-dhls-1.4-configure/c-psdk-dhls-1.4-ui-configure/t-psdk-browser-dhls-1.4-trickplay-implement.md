---
description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de lecture de l’astuce. Pour passer en mode de lecture de l’astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
title: Mise en oeuvre rapide en avant et en arrière
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# Mise en oeuvre rapide en avant et en arrière {#implement-fast-forward-and-rewind}

Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de lecture de l’astuce. Pour passer en mode de lecture de l’astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.

Pour changer de vitesse, vous devez définir une valeur.

1. Passer du mode de lecture normal (1x) au mode de lecture par astuces en définissant la variable `rate` sur la propriété `MediaPlayer` à une valeur autorisée.

   * La variable `MediaPlayerItem` définit les taux de lecture autorisés.
   * TVSDK sélectionne le taux autorisé le plus proche si le taux spécifié n’est pas autorisé.

     Lorsque le taux de trickplay passe de 0 (pause) ou 1 (lecture normale) à un taux supérieur à 1 ou inférieur à -1, toutes les publicités de la chronologie sont supprimées. Il n’existe qu’une seule période sur la chronologie entière qui facilite une action de trickplay pour permettre au contenu d’être rapidement transféré et redémarré sans s’arrêter à n’importe quelle position publicitaire. Cette action est activée par une action de détachement de la chronologie sur TVSDK pour supprimer tous les AdBreaks résolus. Lorsque l’exécution d’un effet trickplay reprend à 0 ou 1, les adBreaks sont d’abord restaurés par l’action de pièce jointe de la chronologie.

     Gardez à l’esprit les informations suivantes :

   * Si l’action de trickplay consiste à revenir en arrière du contenu, la lecture reprend lorsque le taux passe à 1.
   * Si l’action de trickplay consiste à transférer rapidement le contenu, la dernière coupure publicitaire ignorée est lue à la position de reprise.

   Cet exemple définit le taux de lecture interne du lecteur sur le taux demandé.

   ```
   private function onPlaybackRateChange(event:IndexChangeEvent):void { 
       var newRateIndex:int = event.newIndex; 
       var newRate:Number = _playbackRates[newRateIndex]; 
   
       _player.rate = newRate; 
   } 
   ```

1. Vous pouvez éventuellement écouter les événements de changement de taux, qui vous permettent de savoir quand vous avez demandé un changement de taux et quand un changement de taux se produit réellement.

   TVSDK distribue les événements suivants liés à la lecture de l’astuce :

   * `mediacore.events.PlaybackRateEvent.RATE_SELECTED` lorsque la variable `rate` change de valeur.

   * `mediacore.events.PlaybackRateEvent.RATE_PLAYING` lorsque la lecture reprend au rythme sélectionné.

   TVSDK distribue ces deux événements lorsque le lecteur revient du mode de lecture de l’astuce au mode de lecture normal.

## Éléments de l’API de changement de taux {#rate-change-api}

TVSDK comprend des méthodes, des propriétés et des événements pour déterminer des taux valides, des taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au retour arrière.

Utilisez les éléments d’API suivants pour modifier les taux de lecture :

* `MediaPlayer.rate` propriété avec fonctions setter et getter
* `MediaPlayer.localTime property` fonction getter
* `mediacore.events.PlaybackRateEvent.RATE_SELECTED`
* `mediacore.events.PlaybackRateEvent.RATE_PLAYING`
* `MediaPlayerItem.IsTrickPlaySupported` propriété avec fonction getter
* `AdBreakPlaybackEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.availablePlaybackRates` avec la fonction getter - spécifie des taux valides.

| Valeur de taux | Effet sur la lecture |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0  , 128.0 | Passe en mode avance rapide avec le multiplicateur spécifié plus rapide que la normale (par exemple, 4 est 4 fois plus rapide que la normale). |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0  , -128.0 | Bascule vers le mode de retour arrière rapide |
| 1.0 | Passe en mode de lecture normal (appel `play` est identique à la définition de la propriété rate sur 1.0) |
| 0.0 | Pauses (appel `pause` est identique à la définition de la propriété rate sur 0,0) |

## Limites et comportement pour la lecture de l’astuce {#limitations-behavior-trick-play}

Voici les limites du mode de lecture des astuces :

* La liste de lecture principale doit contenir des segments d’image I uniquement. Seules les images clés de la piste d’i-frame s’affichent à l’écran.
* La piste audio et les sous-titres fermés sont désactivés.
* La logique de débit adaptatif (ABR) est désactivée. TVSDK sélectionne un débit entre le débit fourni le plus faible et 800 Kbit/s et l’utilise pendant toute la session de lecture de l’astuce.
* La lecture et la pause sont activées.
* La recherche est refusée. Pour rechercher, appelez `pause` pour quitter le mode de lecture de l’astuce, puis appelez `seek`.

* Vous pouvez quitter le mode de lecture des astuces dans n’importe quel taux de lecture autorisé (lecture ou pause).
* Lorsque des publicités sont intégrées dans la diffusion :

   * Vous pouvez jouer uniquement lors de la lecture du contenu principal. Une erreur est envoyée si vous essayez de basculer vers l’astuce lors d’une coupure publicitaire.
   * Après avoir commencé le mode de lecture des astuces, les coupures publicitaires sont ignorées et aucun événement publicitaire n’est déclenché.
   * La chronologie exposée par TVSDK à l’application du lecteur n’est pas modifiée même si des coupures publicitaires sont ignorées.
   * La variable `MediaPlayer.currentTime` permet d’avancer (à l’avance rapide) ou de reculer (à l’arrière rapide) pendant la durée de la coupure publicitaire ignorée. Ce comportement de saut pour l’heure actuelle permet à la durée du flux de rester inchangée pendant la lecture de l’astuce. Votre application de lecteur peut utiliser la variable `localTime` pour effectuer le suivi du temps relatif uniquement au contenu principal. Aucun saut de temps n’est effectué sur les valeurs renvoyées pour l’heure locale lors de la saut d’une publicité.

   * La variable `AdBreakPlaybackEvent.AD_BREAK_SKIPPED` est distribué immédiatement avant qu’une coupure publicitaire ne soit sur le point d’être ignorée. Votre lecteur peut utiliser cet événement pour implémenter la logique personnalisée liée aux coupures publicitaires ignorées.
   * La sortie d’un jeu de astuces appelle la même stratégie de lecture de publicité que lorsque vous quittez la recherche.

     Par conséquent, comme pour la recherche, le comportement dépend de la différence entre la stratégie de lecture de votre application et la stratégie par défaut. La valeur par défaut est que la dernière coupure publicitaire ignorée est lue au point où vous sortez de la lecture de l’astuce.
