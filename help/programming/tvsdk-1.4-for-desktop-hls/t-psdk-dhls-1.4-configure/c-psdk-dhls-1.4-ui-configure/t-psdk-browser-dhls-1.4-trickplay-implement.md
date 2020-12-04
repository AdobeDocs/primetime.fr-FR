---
description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuces, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
seo-description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuces, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
seo-title: Mise en oeuvre rapide de l’avance et du rembobinage
title: Mise en oeuvre rapide de l’avance et du rembobinage
uuid: bd190534-c871-4673-b79d-1413277f480f
translation-type: tm+mt
source-git-commit: 5a786d8001326f874a51d65b8e8badca44f46e96
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Mettre en oeuvre des processus de transfert et de rembobinage rapides {#implement-fast-forward-and-rewind}

Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuces, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.

Pour changer de vitesse, vous devez définir une valeur.

1. Passez du mode de lecture normal (1x) au mode de lecture fictive en définissant la propriété `rate` sur `MediaPlayer` sur une valeur autorisée.

   * La classe `MediaPlayerItem` définit les taux de lecture autorisés.
   * TVSDK sélectionne le taux autorisé le plus proche si le taux spécifié n’est pas autorisé.

      Lorsque le taux de trickplay passe de 0 (pause) ou 1 (lecture normale) à un taux supérieur à 1 ou inférieur à -1, toutes les publicités du plan de montage chronologique sont supprimées. Il n&#39;y a qu&#39;une seule période sur l&#39;ensemble de la chronologie qui facilite une action de trickplay pour permettre au contenu d&#39;être rapidement transféré et remonté sans s&#39;arrêter à n&#39;importe quelle position publicitaire. Cette action est activée par une action de détachement de la chronologie sur TVSDK pour supprimer toutes les publicitésBreaks résolues. Lorsque le scénario reprend à 0 ou 1, les adBreaks sont d’abord restaurés par l’action de pièce jointe de la chronologie.

      Rappelez-vous des informations suivantes :

   * Si l’action de trickplay consiste à rembobiner le contenu, la lecture reprend lorsque le taux passe à 1.
   * Si l’action de trickplay consiste à avancer rapidement le contenu, la dernière coupure publicitaire ignorée est lue à la position de reprise.

   Cet exemple montre comment définir le taux de lecture interne du lecteur sur le taux demandé.

   ```
   private function onPlaybackRateChange(event:IndexChangeEvent):void { 
       var newRateIndex:int = event.newIndex; 
       var newRate:Number = _playbackRates[newRateIndex]; 
   
       _player.rate = newRate; 
   } 
   ```

1. Vous pouvez éventuellement écouter les événements de changement de taux, ce qui vous permet de savoir quand vous avez demandé un changement de taux et quand un changement de taux se produit réellement.

   TVSDK distribue les événements suivants liés au jeu vidéo :

   * `mediacore.events.PlaybackRateEvent.RATE_SELECTED` lorsque la  `rate` valeur change.

   * `mediacore.events.PlaybackRateEvent.RATE_PLAYING` lorsque la lecture reprend au rythme sélectionné.

   TVSDK distribue ces deux événements lorsque le lecteur revient du mode de lecture de l’astuce au mode de lecture normal.

## Eléments API de changement de taux {#rate-change-api}

TVSDK comprend des méthodes, des propriétés et des événements permettant de déterminer les taux valides, les taux courants, la prise en charge ou non de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au rembobinage.

Utilisez les éléments d’API suivants pour modifier les taux de lecture :

* `MediaPlayer.rate` propriété avec les fonctions setter et getter
* `MediaPlayer.localTime property` avec la fonction getter
* `mediacore.events.PlaybackRateEvent.RATE_SELECTED`
* `mediacore.events.PlaybackRateEvent.RATE_PLAYING`
* `MediaPlayerItem.IsTrickPlaySupported` propriété avec la fonction getter
* `AdBreakPlaybackEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.availablePlaybackRates` propriété avec la fonction getter - spécifie des tarifs valides.

| Valeur de taux | Effet sur la lecture |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Bascule en mode avance rapide avec le multiplicateur spécifié plus rapide que la normale (par exemple, 4 fois plus rapide que la normale) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0, -128.0 | Bascule en mode de rembobinage rapide |
| 1,0 | Bascule en mode de lecture normal (appeler `play` revient à définir la propriété rate sur 1.0) |
| 0,0 | Interruptions (appeler `pause` revient à définir la propriété rate sur 0,0) |

## Limites et comportement pour le jeu vidéo {#limitations-behavior-trick-play}

Voici les limites du mode de lecture des astuces :

* La liste de lecture principale doit contenir des segments d’image I uniquement. Seules les images clés de la piste I-frame s’affichent à l’écran.
* La piste audio et les légendes fermées sont désactivées.
* La logique ABR (Adaptive Bbit Rate) est désactivée. TVSDK sélectionne un débit entre le débit fourni le plus faible et 800 kbit/s et l’utilise pendant toute la session de lecture.
* La lecture et la mise en pause sont activées.
* La recherche est interdite. Pour effectuer une recherche, appelez `pause` pour quitter le mode de lecture de l&#39;astuce, puis appelez `seek`.

* Vous pouvez quitter le mode de lecture par astuces pour n’importe quel taux de lecture autorisé (lecture ou pause).
* Lorsque des publicités sont incorporées dans le flux :

   * Vous pouvez jouer uniquement lors de la lecture du contenu principal. Une erreur est diffusée si vous tentez de basculer vers l’astuce au cours d’une coupure publicitaire.
   * Après avoir commencé le mode de lecture des astuces, les coupures publicitaires sont ignorées et aucun événement publicitaire n’est déclenché.
   * La chronologie exposée par TVSDK à l’application du lecteur n’est pas modifiée même si des coupures publicitaires sont ignorées.
   * La propriété `MediaPlayer.currentTime` saute vers l’avant (en avant rapide) ou vers l’arrière (en arrière rapide) avec la durée de la coupure publicitaire ignorée. Ce comportement de saut pour l’heure actuelle permet à la durée du flux de rester inchangée pendant la lecture de l’astuce. Votre application de lecteur peut utiliser la propriété `localTime` pour effectuer le suivi de l’heure par rapport au contenu principal uniquement. Les sauts de temps ne sont pas effectués sur les valeurs renvoyées pour l’heure locale lors de l’abandon d’une publicité.

   * Le événement `AdBreakPlaybackEvent.AD_BREAK_SKIPPED` est distribué immédiatement avant qu’une coupure publicitaire ne soit sur le point d’être ignorée. Votre lecteur peut utiliser ce événement pour implémenter une logique personnalisée liée aux coupures publicitaires ignorées.
   * La sortie d’un jeu vidéo appelle la même stratégie de lecture publicitaire que lors de la sortie de la recherche.

      Par conséquent, comme dans le cas de la recherche, le comportement dépend de la différence entre la stratégie de lecture de l’application et la stratégie par défaut. La valeur par défaut est que la dernière coupure publicitaire sautée est lue à l’endroit où vous sortez de la lecture de l’astuce.