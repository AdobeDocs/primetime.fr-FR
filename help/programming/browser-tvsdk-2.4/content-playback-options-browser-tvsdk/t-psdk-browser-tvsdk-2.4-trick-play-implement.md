---
description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuces, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
seo-description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuces, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
seo-title: Mise en oeuvre rapide de l’avance et du rembobinage
title: Mise en oeuvre rapide de l’avance et du rembobinage
uuid: c1992757-d067-4c11-8d08-fec09099476f
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Mise en oeuvre rapide de l’avance et du rembobinage{#implement-fast-forward-and-rewind}

Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuces, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.

>[!IMPORTANT]
>
>* Le mode de lecture des images par bandes est pris en charge uniquement pour le contenu VOD MPEG et HLS.
>* Le mode de lecture de la vidéo n’est pas pris en charge pour les flux en direct ou les publicités.
>* Lorsque vous passez du contenu principal à une publicité, le navigateur TVSDK quitte le mode de lecture des astuces.
>



Pour changer de vitesse, vous devez définir une valeur.

1. Passez du mode de lecture normal (1x) au mode de lecture par astuces en définissant le taux sur le `MediaPlayer` à une valeur autorisée.

   * La `MediaPlayerItem` classe définit les taux de lecture autorisés.
   * Le navigateur TVSDK sélectionne le taux autorisé le plus proche si le taux spécifié n’est pas autorisé.

      L’exemple de fonction suivant définit le taux :

      ```js
      setTrickPlayRate = function (player, trickPlayRate) { 
                    player.rate = trickPlayRate; 
      }
      ```

      L’exemple de fonction suivant peut être utilisé pour requête les taux de lecture disponibles :

      ```js
      getAvailableTrickPlayRates = function (player) { 
               var item = player.currentItem; 
               var availableRates = item. availablePlaybackRates; 
               return availableRates; 
      } 
      ```

1. Vous pouvez éventuellement écouter les événements de changement de taux, ce qui vous permet de savoir quand vous avez demandé un changement de taux et quand un changement de taux se produit réellement.

       Le navigateur TVSDK distribue les événements suivants liés à la lecture de l’astuce :
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` lorsque la `rate` valeur change.

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` lorsque la lecture reprend au rythme sélectionné.

      Le navigateur TVSDK distribue ces deux événements lorsque le lecteur revient du mode de lecture de l’astuce au mode de lecture normal.

## Eléments API de changement de taux {#rate-change-API-elements}

Le kit TVSDK du navigateur comprend des méthodes, des propriétés et des événements permettant de déterminer les taux valides, les taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités liées à l’avance rapide et au rembobinage.

Utilisez les éléments d’API suivants pour modifier les taux de lecture :

* `MediaPlayer.rate`
* `PlaybackRateEvent.rate`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerItem.availablePlaybackRates` - indique des tarifs valides.

   | Valeur de taux | Effet sur la lecture |
   |---|---|
   | 2.0, 4.0, 8.0, 16.0, 32.0, 64.0 | Bascule en mode avance rapide avec le multiplicateur spécifié plus rapide que la normale (par exemple, 4 fois plus rapide que la normale) |
   | -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 | Bascule en mode de rembobinage rapide |
   | 1.0 | Bascule en mode de lecture normal (appeler `play` revient à définir la propriété rate sur 1,0) |
   | 0.0 | Interruptions (l’appel `pause` est identique à la définition de la propriété rate sur 0,0) |

## Limites et comportement pour le jeu vidéo {#limitations-and-behavior-trick-play}

Il y a certaines limites et certains problèmes dans le comportement du mode de jeu de l&#39;astuce.

Voici une liste des limitations du mode de jeu vidéo :

* Si le flux ne contient pas d&#39;adaptation de jeu de tour, le rembobinage rapide est désactivé et le taux de jeu maximal pour l&#39;avance rapide est limité à 8.
* Lorsque des adaptations de la lecture de l&#39;astuce sont utilisées pour fournir le mode de l&#39;astuce, la piste audio est désactivée.
* En mode de lecture de l’astuce, le changement de pistes audio et de sous-titres fermés est désactivé.
* La lecture et la mise en pause sont activées.
* Lors de la recherche, si la lecture est en mode de lecture par astuces, le taux de lecture est défini sur 1 et la lecture normale reprend.
* La logique de débit binaire adaptatif (ABR) est activée.

   Lors de l&#39;utilisation d&#39;adaptations normales, les profils sont limités entre `ABRControlParameters.minBitRate` et `ABRControlParameters.maxBitRate`. Lorsque vous utilisez des adaptations de jeux de ficelles, les profils sont limités entre `ABRControlParameters.minTrickPlayBitRate` et `ABRControlParameters.maxTrickPlayBitRate`.