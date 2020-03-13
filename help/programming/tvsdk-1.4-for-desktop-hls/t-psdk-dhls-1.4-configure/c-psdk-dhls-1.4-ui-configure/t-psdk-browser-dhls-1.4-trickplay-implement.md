---
description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
seo-description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
seo-title: Mise en oeuvre rapide de l’avance et du retour en arrière
title: Mise en oeuvre rapide de l’avance et du retour en arrière
uuid: bd190534-c871-4673-b79d-1413277f480f
translation-type: tm+mt
source-git-commit: 5a786d8001326f874a51d65b8e8badca44f46e96

---


# Mise en oeuvre rapide de l’avance et du retour en arrière {#implement-fast-forward-and-rewind}

Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.

Pour changer de vitesse, vous devez définir une valeur.

1. Passez du mode de lecture normal (1x) au mode de lecture fictive en définissant la `rate` propriété sur la `MediaPlayer` valeur autorisée.

   * La `MediaPlayerItem` classe définit les taux de lecture autorisés.
   * TVSDK sélectionne le taux autorisé le plus proche si le taux spécifié n’est pas autorisé.

      Lorsque le taux de trickplay passe de 0 (pause) ou 1 (lecture normale) à un taux supérieur à 1 ou inférieur à -1, toutes les publicités du plan de montage chronologique sont supprimées. Il n’y a qu’une seule période sur l’ensemble du plan de montage chronologique qui facilite une action de trickplay pour permettre le transfert rapide du contenu et sa remise en route sans s’arrêter à une position publicitaire. Cette action est activée par une action de détachement du plan de montage chronologique sur TVSDK pour supprimer tous les AdBreaks résolus. Lorsque le scénario reprend à 0 ou 1, les pauses publicitaires sont tout d’abord restaurées par l’action de pièce jointe de la chronologie.

      Tenez compte des informations suivantes :

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

1. Vous pouvez éventuellement écouter les  de changement de taux, qui vous indiquent quand vous avez demandé un changement de taux et quand un changement de taux se produit.

   TVSDK distribue le  suivant en rapport avec le jeu vidéo :

   * `mediacore.events.PlaybackRateEvent.RATE_SELECTED` lorsque la `rate` valeur change.

   * `mediacore.events.PlaybackRateEvent.RATE_PLAYING` lorsque la lecture reprend au rythme sélectionné.
   TVSDK distribue ces deux  lorsque le lecteur revient du mode de jeu de l’astuce au mode de jeu normal.

## Eléments de l’API de changement de taux {#rate-change-api}

TVSDK comprend des méthodes, des propriétés et des  pour déterminer les taux valides, les taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au retour arrière.

Utilisez les éléments d’API suivants pour modifier les taux de lecture :

* `MediaPlayer.rate` propriété avec les fonctions setter et getter
* `MediaPlayer.localTime property` avec getter, fonction
* `mediacore.events.PlaybackRateEvent.RATE_SELECTED`
* `mediacore.events.PlaybackRateEvent.RATE_PLAYING`
* `MediaPlayerItem.IsTrickPlaySupported` propriété avec la fonction getter
* `AdBreakPlaybackEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.availablePlaybackRates` propriété avec la fonction getter - indique des taux valides.

| Valeur de taux | Effet sur la lecture |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0  , 128.0 | Bascule en mode avance rapide avec le multiplicateur spécifié plus rapide que la normale (par exemple, 4 fois plus rapide que la normale) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0  , -128.0 | Bascule en mode Rembobinage rapide |
| 1.0 | Bascule en mode de lecture normal (l’appel `play` équivaut à définir la propriété rate sur 1,0) |
| 0.0 | Interrompt (l’appel `pause` équivaut à définir la propriété rate sur 0,0) |

## Limites et comportement pour le jeu par astuces {#limitations-behavior-trick-play}

Voici les limites du mode de jeu par astuces :

* La liste de lecture principale doit contenir des segments d’image I uniquement. Seules les images clés de la piste I-frame s’affichent à l’écran.
* La piste audio et les sous-titres sont désactivés.
* La logique ABR (Adaptive bit rate) est désactivée. TVSDK sélectionne un débit entre le débit fourni le plus faible et 800 kbit/s et l’utilise pendant toute la session de jeu vidéo.
* La lecture et la mise en pause sont activées.
* La recherche est refusée. Pour effectuer une recherche, appelez `pause` pour quitter le mode de jeu par astuce, puis appelez `seek`.

* Vous pouvez quitter le mode de lecture par astuce dans n’importe quel taux de lecture autorisé (lecture ou pause).
* Lorsque des publicités sont intégrées au flux :

   * Vous pouvez jouer uniquement lors de la lecture du contenu principal. Une erreur est diffusée si vous tentez de basculer vers l’astuce play pendant une coupure publicitaire.
   * Après avoir démarré le mode de lecture par astuce, les coupures publicitaires sont ignorées et aucun publicitaire n’est déclenché.
   * La chronologie exposée par TVSDK à l’application du lecteur n’est pas modifiée, même si les coupures publicitaires sont ignorées.
   * La `MediaPlayer.currentTime` propriété saute vers l’avant (en avant rapide) ou vers l’arrière (en arrière rapide) avec la durée de la coupure publicitaire sautée. Ce comportement de saut pour l’instant présent permet à la durée du flux de rester inchangée pendant la lecture de l’astuce. Votre application de lecteur peut utiliser la `localTime` propriété pour effectuer le suivi de la durée relative au contenu principal uniquement. Les sauts de temps ne sont pas effectués sur les valeurs renvoyées pour l’heure locale lors de la saut d’une publicité.

   * Le  `AdBreakPlaybackEvent.AD_BREAK_SKIPPED` est distribué immédiatement avant qu’une coupure publicitaire ne soit sur le point d’être ignorée. Votre lecteur peut utiliser ce pour implémenter la logique personnalisée liée aux coupures publicitaires ignorées.
   * La sortie d’un jeu de astuces appelle la même stratégie de lecture de publicité que lors de la sortie de la recherche.

      Par conséquent, comme dans le cas de la recherche, le comportement dépend de la différence entre la stratégie de lecture de votre application et la stratégie par défaut. La valeur par défaut est que la dernière coupure publicitaire sautée est lue au point où vous sortez de la lecture de l’astuce.