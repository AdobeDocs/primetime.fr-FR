---
description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
seo-description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
seo-title: Mise en oeuvre rapide de l’avance et du retour en arrière
title: Mise en oeuvre rapide de l’avance et du retour en arrière
uuid: c1992757-d067-4c11-8d08-fec09099476f
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Mise en oeuvre rapide de l’avance et du retour en arrière{#implement-fast-forward-and-rewind}

Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.

>[!IMPORTANT]
>
>* Le mode de lecture des vidéos à l’écran est uniquement pris en charge pour le contenu VOD MPEG Dash et HLS.
>* Le mode de lecture en vidéo n’est pas pris en charge pour les flux en direct ou les publicités.
>* Lorsque vous passez d’un contenu principal à une publicité, le navigateur TVSDK quitte le mode de lecture des astuces.
>



Pour changer de vitesse, vous devez définir une valeur.

1. Passez du mode de lecture normal (1x) au mode de lecture fictive en définissant le taux sur la valeur `MediaPlayer` autorisée.

   * La `MediaPlayerItem` classe définit les taux de lecture autorisés.
   * Le navigateur TVSDK sélectionne le taux autorisé le plus proche si le taux spécifié n’est pas autorisé.

      L’exemple de fonction suivant définit le taux :

      ```js
      setTrickPlayRate = function (player, trickPlayRate) { 
                    player.rate = trickPlayRate; 
      }
      ```

      L’exemple de fonction suivant peut être utilisé pour  les taux de lecture disponibles :

      ```js
      getAvailableTrickPlayRates = function (player) { 
               var item = player.currentItem; 
               var availableRates = item. availablePlaybackRates; 
               return availableRates; 
      } 
      ```

1. Vous pouvez éventuellement écouter les  de changement de taux, qui vous indiquent quand vous avez demandé un changement de taux et quand un changement de taux se produit.

       Le navigateur TVSDK distribue le  suivant en rapport avec le jeu vidéo :
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` lorsque la `rate` valeur change.

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` lorsque la lecture reprend au rythme sélectionné.

      Le navigateur TVSDK distribue ces deux  lorsque le lecteur revient du mode de jeu de l’astuce au mode de lecture normal.

## Eléments de l’API de changement de taux {#rate-change-API-elements}

Le SDK du navigateur comprend des méthodes, des propriétés et des  pour déterminer les taux valides, les taux actuels, la prise en charge de la lecture par astuce et d’autres fonctionnalités liées à l’avance rapide et au retour arrière.

Utilisez les éléments d’API suivants pour modifier les taux de lecture :

* `MediaPlayer.rate`
* `PlaybackRateEvent.rate`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerItem.availablePlaybackRates` - indique les taux valides.

   | Valeur de taux | Effet sur la lecture |
   |---|---|
   | 2.0, 4.0, 8.0, 16.0, 32.0, 64.0 | Bascule en mode avance rapide avec le multiplicateur spécifié plus rapide que la normale (par exemple, 4 fois plus rapide que la normale) |
   | -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 | Bascule en mode Rembobinage rapide |
   | 1.0 | Bascule en mode de lecture normal (l’appel `play` équivaut à définir la propriété rate sur 1,0) |
   | 0.0 | Interrompt (l’appel `pause` équivaut à définir la propriété rate sur 0,0) |

## Limitations et comportement pour le jeu de ficelles {#limitations-and-behavior-trick-play}

Il y a certaines limites et certains problèmes dans le comportement du mode de jeu par les tours.

Voici un  des limitations du mode de jeu par la ruse :

* Si le flux ne contient pas d&#39;adaptation de jeu de tour, le rembobinage rapide est désactivé et le taux de lecture maximal pour l&#39;avance rapide est limité à 8.
* Lorsque des adaptations de la lecture de l’astuce sont utilisées pour fournir le mode de l’astuce, la piste audio est désactivée.
* En mode de lecture de l’astuce, le basculement des pistes audio et des sous-titres est désactivé.
* La lecture et la mise en pause sont activées.
* Lors de la recherche, si la lecture est en mode de lecture par astuce, le taux de lecture est défini sur 1 et la lecture normale reprend.
* La logique ABR (Adaptive bit rate) est activée.

   Lors de l&#39;utilisation d&#39;adaptations normales, les  sont restreintes entre `ABRControlParameters.minBitRate` et `ABRControlParameters.maxBitRate`. Lors de l’utilisation des adaptations de jeux de ficelles, les sont limités entre `ABRControlParameters.minTrickPlayBitRate` et `ABRControlParameters.maxTrickPlayBitRate`.