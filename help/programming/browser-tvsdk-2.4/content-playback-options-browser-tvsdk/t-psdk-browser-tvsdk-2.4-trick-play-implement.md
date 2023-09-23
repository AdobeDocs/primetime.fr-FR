---
description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de lecture de l’astuce. Pour passer en mode de lecture de l’astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
title: Mise en oeuvre rapide en avant et en arrière
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Mise en oeuvre rapide en avant et en arrière{#implement-fast-forward-and-rewind}

Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de lecture de l’astuce. Pour passer en mode de lecture de l’astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.

>[!IMPORTANT]
>
>* Le mode de lecture des corbeilles est pris en charge uniquement pour le contenu MPEG Dash et HLS VOD.
>* Le mode de lecture de l’aperçu n’est pas pris en charge pour les diffusions en direct ou les publicités.
>* Lors du passage du contenu principal à une publicité, le TVSDK du navigateur quitte le mode de lecture de l’astuce.
>

Pour changer de vitesse, vous devez définir une valeur.

1. Passer du mode de lecture normal (1x) au mode de lecture astucieux en définissant le taux sur la `MediaPlayer` à une valeur autorisée.

   * La variable `MediaPlayerItem` définit les taux de lecture autorisés.
   * Le TVSDK du navigateur sélectionne le taux autorisé le plus proche si le taux spécifié n’est pas autorisé.

     L’exemple de fonction suivant définit le taux :

     ```js
     setTrickPlayRate = function (player, trickPlayRate) { 
                   player.rate = trickPlayRate; 
     }
     ```

     L’exemple de fonction suivant peut être utilisé pour interroger les taux de lecture disponibles :

     ```js
     getAvailableTrickPlayRates = function (player) { 
              var item = player.currentItem; 
              var availableRates = item. availablePlaybackRates; 
              return availableRates; 
     } 
     ```

1. Vous pouvez éventuellement écouter les événements de changement de taux, qui vous permettent de savoir quand vous avez demandé un changement de taux et quand un changement de taux se produit réellement.

       Le navigateur TVSDK distribue les événements suivants liés à la lecture de l’astuce :
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` lorsque la variable `rate` change de valeur.

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` lorsque la lecture reprend au rythme sélectionné.

     Le navigateur TVSDK distribue ces deux événements lorsque le lecteur revient du mode de lecture de l’astuce au mode de lecture normal.

## Éléments de l’API de changement de taux {#rate-change-API-elements}

La technologie TVSDK du navigateur comprend des méthodes, des propriétés et des événements pour déterminer des taux valides, des taux actuels, la prise en charge de la lecture de l’astuce et d’autres fonctionnalités relatives à l’avance rapide et au retour arrière.

Utilisez les éléments d’API suivants pour modifier les taux de lecture :

* `MediaPlayer.rate`
* `PlaybackRateEvent.rate`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerItem.availablePlaybackRates` - indique des taux valides.

  | Valeur de taux | Effet sur la lecture |
  |---|---|
  | 2.0, 4.0, 8.0, 16.0, 32.0, 64.0 | Passe en mode avance rapide avec le multiplicateur spécifié plus rapide que la normale (par exemple, 4 est 4 fois plus rapide que la normale). |
  | -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 | Bascule vers le mode de retour arrière rapide |
  | 1.0 | Passe en mode de lecture normal (appel `play` est identique à la définition de la propriété rate sur 1.0) |
  | 0.0 | Pauses (appel `pause` est identique à la définition de la propriété rate sur 0,0) |

## Limites et comportement du jeu vidéo {#limitations-and-behavior-trick-play}

Il existe certaines limites et certains problèmes dans le comportement du mode de lecture des astuces.

Voici une liste des restrictions du mode de lecture des astuces :

* Si le flux ne contient pas d’adaptation de lecture de l’astuce, le rembobinage rapide est désactivé et le taux de lecture maximal pour un transfert rapide est limité à 8.
* Lorsque des adaptations de lecture de l’astuce sont utilisées pour fournir le mode de l’astuce, la piste audio est désactivée.
* En mode de lecture de l’astuce, le changement de suivi du son et des sous-titres fermés est désactivé.
* La lecture et la pause sont activées.
* Lors de la recherche, si la lecture est en mode de lecture de l’astuce, le taux de lecture est défini sur 1 et la lecture normale reprend.
* La logique de débit adaptatif (ABR) est activée.

  Lors de l’utilisation d’adaptations normales, les profils sont restreints entre `ABRControlParameters.minBitRate` et `ABRControlParameters.maxBitRate`. Lors de l’utilisation d’adaptations de jeux vidéo, les profils sont restreints entre `ABRControlParameters.minTrickPlayBitRate` et `ABRControlParameters.maxTrickPlayBitRate`.
