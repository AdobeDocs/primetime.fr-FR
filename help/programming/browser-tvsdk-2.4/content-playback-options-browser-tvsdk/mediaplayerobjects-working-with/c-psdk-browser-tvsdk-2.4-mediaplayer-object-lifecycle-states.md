---
description: Depuis le moment où l’instance MediaPlayer est créée jusqu’au moment où elle est terminée, cette instance se transition d’un état à l’autre.
title: Cycle de vie et états de l’objet MediaPlayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# Cycle de vie et états de l’objet MediaPlayer{#life-cycle-and-states-of-the-mediaplayer-object}

Depuis le moment où l’instance MediaPlayer est créée jusqu’au moment où elle est terminée, cette instance se transition d’un état à l’autre.

Voici quelques exemples :

* **IDLE** :  `MediaPlayerStatus.IDLE`

* **INITIALISATION** :  `MediaPlayerStatus.INITIALIZING`

* **INITIALISÉ** :  `MediaPlayerStatus.INITIALIZED`

* **PRÉPARATION** :  `MediaPlayerStatus.PREPARING`

* **PRÉPARÉ** :  `MediaPlayerStatus.PREPARED`

* **LECTURE** :  `MediaPlayerStatus.PLAYING`

* **EN PAUSE** :  `MediaPlayerStatus.PAUSED`

* **RECHERCHE** :  `MediaPlayerStatus.SEEKING`

* **TERMINÉ** :  `MediaPlayerStatus.COMPLETE`

* **ERREUR** :  `MediaPlayerStatus.ERROR`

* **PUBLIÉ** :  `MediaPlayerStatus.RELEASED`

La liste complète des états est définie dans `MediaPlayerStatus`.

Il est utile de connaître l’état du lecteur car certaines opérations ne sont autorisées que lorsque le lecteur se trouve dans un état particulier. Par exemple, `play` ne peut pas être appelé pendant l&#39;état IDLE. Elle doit être appelée après avoir atteint l’état PRÉPARÉ. L’état ERROR modifie également ce qui peut se passer ensuite.

Lorsqu’une ressource multimédia est chargée et lue, le lecteur se transition de la manière suivante :

1. L’état initial est IDLE.
1. Votre application appelle `MediaPlayer.replaceCurrentResource`, ce qui déplace le lecteur à l’état INITIALISATION.
1. Si le navigateur TVSDK charge correctement la ressource, l’état devient INITIALISÉ.
1. Votre application appelle `MediaPlayer.prepareToPlay` et l&#39;état devient PRÉPARATION.
1. Le navigateur TVSDK prépare le flux média et début la résolution et l’insertion de publicités (si activé).

   Une fois cette étape terminée, les publicités sont insérées dans la chronologie ou la procédure publicitaire a échoué et l&#39;état du lecteur devient PRÉPARÉ.
1. Lorsque votre application lit et interrompt le média, l’état passe de LECTURE à PAUSED.

   >[!TIP]
   >
   >Lors de la lecture ou de la mise en pause, lorsque vous quittez la lecture, arrêtez le périphérique ou changez d’application, l’état est SUSPENDU et les ressources sont libérées. Pour continuer, restaurez le lecteur multimédia.

1. Lorsque le lecteur atteint la fin du flux, l’état devient COMPLET.
1. Lorsque votre application relâche le lecteur multimédia, l’état devient RELÂCHÉ.
1. Si une erreur se produit pendant le processus, l’état devient ERROR.

Voici une illustration du cycle de vie d’une instance MediaPlayer :

<!--<a id="fig_DD3DAE7507C549C8A4720A26DFCFFCCB"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

Vous pouvez utiliser l’état pour fournir des commentaires à l’utilisateur sur le processus (par exemple, un analyseur en attendant le changement d’état suivant) ou pour suivre les étapes suivantes de lecture du média, par exemple attendre l’état approprié avant d’appeler la méthode suivante.

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

