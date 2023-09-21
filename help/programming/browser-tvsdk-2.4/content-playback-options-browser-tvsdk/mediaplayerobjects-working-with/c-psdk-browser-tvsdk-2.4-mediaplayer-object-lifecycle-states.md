---
description: À partir du moment où l’instance MediaPlayer est créée et jusqu’au moment où elle est arrêtée, cette instance passe d’un état à l’autre.
title: Cycle de vie et états de l’objet MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Cycle de vie et états de l’objet MediaPlayer{#life-cycle-and-states-of-the-mediaplayer-object}

À partir du moment où l’instance MediaPlayer est créée et jusqu’au moment où elle est arrêtée, cette instance passe d’un état à l’autre.

Voici les états possibles :

* **IDLE**: `MediaPlayerStatus.IDLE`

* **INITIALISATION**: `MediaPlayerStatus.INITIALIZING`

* **INITIALIZED**: `MediaPlayerStatus.INITIALIZED`

* **PRÉPARATION**: `MediaPlayerStatus.PREPARING`

* **PRÉPARÉ**: `MediaPlayerStatus.PREPARED`

* **LECTURE**: `MediaPlayerStatus.PLAYING`

* **PAUSED**: `MediaPlayerStatus.PAUSED`

* **RECHERCHE**: `MediaPlayerStatus.SEEKING`

* **TERMINER**: `MediaPlayerStatus.COMPLETE`

* **ERROR**: `MediaPlayerStatus.ERROR`

* **PUBLIÉ**: `MediaPlayerStatus.RELEASED`

La liste complète des états est définie dans `MediaPlayerStatus`.

Connaître l’état du lecteur est utile, car certaines opérations ne sont autorisées que lorsque le lecteur se trouve dans un état particulier. Par exemple : `play` ne peut pas être appelé alors qu’il est à l’état IDLE. Il doit être appelé après avoir atteint l’état PRÉPARÉ . L’état ERROR modifie également ce qui peut se produire ensuite.

Lorsqu’une ressource multimédia est chargée et lue, le lecteur évolue comme suit :

1. L’état initial est IDLE.
1. Vos appels d’application `MediaPlayer.replaceCurrentResource`, qui déplace le lecteur à l’état INITIALISATION .
1. Si le Browser TVSDK charge correctement la ressource, l’état devient INITIALIZED.
1. Vos appels d’application `MediaPlayer.prepareToPlay`et l’état devient PRÉPARATION.
1. Le navigateur TVSDK prépare le flux multimédia et lance la résolution de la publicité et l’insertion de publicités (s’il est activé).

   Une fois cette étape terminée, les publicités sont insérées dans la chronologie ou la procédure de publicité a échoué, et l’état du lecteur passe à PRÉPARÉ.
1. Lorsque votre application est lue et met le média en pause, l’état se déplace entre LECTURE et PAUSE.

   >[!TIP]
   >
   >Lors de la lecture ou de la mise en pause, lorsque vous quittez la lecture, arrêtez l’appareil ou changez d’application, l’état devient SUSPENDU et les ressources sont publiées. Pour continuer, restaurez le lecteur multimédia.

1. Lorsque le lecteur atteint la fin de la diffusion, l’état devient TERMINÉ.
1. Lorsque votre application relâche le lecteur multimédia, l’état devient LIBÉRÉ.
1. Si une erreur se produit pendant le processus, l’état devient ERROR.

Voici une illustration du cycle de vie d’une instance MediaPlayer :

<!--<a id="fig_DD3DAE7507C549C8A4720A26DFCFFCCB"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

Vous pouvez utiliser l’état pour fournir des commentaires à l’utilisateur sur le processus (par exemple, un compteur en attendant le changement d’état suivant) ou pour prendre les prochaines étapes de lecture du média, comme attendre l’état approprié avant d’appeler la méthode suivante.

Par exemple :

```js
function onStateChanged(state) { 
    switch(state) { 
        // It is recommended that you call prepareToPlay()  
        // after receiving the INITIALIZED state             
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            mediaPlayer.prepareToPlay(); 
            break; 
    } 
} 
```
