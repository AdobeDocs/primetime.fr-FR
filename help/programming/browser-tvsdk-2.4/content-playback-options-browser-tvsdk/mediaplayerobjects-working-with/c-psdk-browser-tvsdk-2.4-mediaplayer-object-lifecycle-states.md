---
description: À partir du moment où l’instance MediaPlayer est créée et jusqu’au moment où elle se termine, cette instance  d’un état à l’autre.
seo-description: À partir du moment où l’instance MediaPlayer est créée et jusqu’au moment où elle se termine, cette instance  d’un état à l’autre.
seo-title: Cycle de vie et états de l’objet MediaPlayer
title: Cycle de vie et états de l’objet MediaPlayer
uuid: fe76ea80-aaa8-43bc-9b81-85e0551f70dd
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Cycle de vie et états de l’objet MediaPlayer{#life-cycle-and-states-of-the-mediaplayer-object}

À partir du moment où l’instance MediaPlayer est créée et jusqu’au moment où elle se termine, cette instance  d’un état à l’autre.

Voici quelques exemples :

* **IDLE**: `MediaPlayerStatus.IDLE`

* **INITIALISATION**: `MediaPlayerStatus.INITIALIZING`

* **INITIALISÉ**: `MediaPlayerStatus.INITIALIZED`

* **PRÉPARATION**: `MediaPlayerStatus.PREPARING`

* **PRÉPARÉ**: `MediaPlayerStatus.PREPARED`

* **LECTURE**: `MediaPlayerStatus.PLAYING`

* **EN PAUSE**: `MediaPlayerStatus.PAUSED`

* **RECHERCHE**: `MediaPlayerStatus.SEEKING`

* **TERMINÉ**: `MediaPlayerStatus.COMPLETE`

* **ERREUR**: `MediaPlayerStatus.ERROR`

* **PUBLIÉ**: `MediaPlayerStatus.RELEASED`

L’ complet des états est défini dans `MediaPlayerStatus`.

Connaître l’état du lecteur est utile car certaines opérations ne sont autorisées que lorsque le lecteur se trouve dans un état particulier. Par exemple, `play` ne peut pas être appelé pendant l’état IDLE. Elle doit être appelée après avoir atteint l’état PRÉPARÉ. L’état ERROR modifie également ce qui peut se passer ensuite.

Lorsqu’une ressource multimédia est chargée et lue, le lecteur  de la manière suivante :

1. L’état initial est IDLE.
1. Votre application appelle `MediaPlayer.replaceCurrentResource`, ce qui déplace le lecteur vers l’état INITIALISATION.
1. Si le navigateur TVSDK charge correctement la ressource, l’état devient INITIALIZED.
1. Votre application appelle `MediaPlayer.prepareToPlay`, et l’état devient PRÉPARATION.
1. Le navigateur TVSDK prépare le flux média et le à la résolution de la publicité et à l’insertion de la publicité (s’il est activé).

   Une fois cette étape terminée, les publicités sont insérées dans le plan de montage chronologique ou la procédure publicitaire a échoué et l’état du lecteur devient PRÉPARÉ.
1. Lorsque votre application est lue et met en pause le média, l’état passe de LECTURE à PAUSE.

   >[!TIP]
   >
   >Lors de la lecture ou de la mise en pause, lorsque vous quittez la lecture, arrêtez le périphérique ou changez d’application, l’état est SUSPENDU et les ressources sont libérées. Pour continuer, restaurez le lecteur multimédia.

1. Lorsque le lecteur atteint la fin du flux, l’état est TERMINÉ.
1. Lorsque votre application relâche le lecteur multimédia, l’état devient LIBÉRÉ.
1. Si une erreur se produit pendant le processus, l’état devient ERROR.

Voici une illustration du cycle de vie d’une instance MediaPlayer :

<!--<a id="fig_DD3DAE7507C549C8A4720A26DFCFFCCB"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

Vous pouvez utiliser l’état pour fournir des commentaires à l’utilisateur sur le processus (par exemple, un compteur en attendant le changement d’état suivant) ou pour passer aux étapes suivantes lors de la lecture du média, comme attendre l’état approprié avant d’appeler la méthode suivante.

Par exemple :

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

