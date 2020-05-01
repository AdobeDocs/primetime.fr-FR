---
description: Le navigateur TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions en fonction des événements de la séquence prévue.
seo-description: Le navigateur TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions en fonction des événements de la séquence prévue.
seo-title: Ordre des événements de lecture
title: Ordre des événements de lecture
uuid: 259a9a2d-3d28-4240-b392-cc81f5c3f0cf
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Ordre des événements de lecture{#order-of-playback-events}

Le navigateur TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions en fonction des événements de la séquence prévue.

<!--<a id="section_D247A5873A854A079EFA6AC2E80AB894"></a>-->

Les exemples suivants montrent l’ordre de certains événements incluant des événements de lecture.

* Lors du chargement réussi d&#39;une ressource multimédia par `replaceCurrentResource`l&#39;intermédiaire de, l&#39;ordre des événements est le suivant :

   * `AdobePSDK.MediaPlayerStatusChangeEvent` with `event.status =`

      * `MediaPlayerStatus.INITIALIZING`
      * `MediaPlayerStatus.INITIALIZED`

* Lors de la préparation de la lecture à travers `MediaPlayer.prepareToPlay`la vidéo, l’ordre des événements est le suivant :

   * `AdobePSDK.MediaPlayerStatusChangeEvent` with `event.status =`

      * `MediaPlayerStatus.PREPARING`
      * `MediaPlayerStatus.PREPARED`

<!--<a id="section_76C13548AF934868B70757CA5489E516"></a>-->

L’exemple suivant illustre une progression type des événements :

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                 onStatusChange); 
 
onStatusChange = function (event) { 
 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.IDLE: 
            console.log("Player Status: IDLE"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.INITIALIZING: 
            console.log("Player Status: INITIALIZING"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            console.log("Player Status: INITIALIZED"); 
            player.prepareToPlay(); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PREPARING: 
            console.log("Player Status: PREPARING"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PREPARED: 
            console.log("Player Status: PREPARED"); 
            if (autoPlay) { 
                player.play(); 
            } 
            else { 
                dispatchEvent(ReferencePlayer.Events.PreparedEvent,  
                              {target: this}); 
            } 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PLAYING: 
            console.log("Player Status: PLAYING"); 
            //update UI play/pause to show pause icon 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PAUSED: 
            console.log("Player Status: PAUSED"); 
            //update UI play/pause to show play icon &  
            //display pause icon over video 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.SEEKING: 
            console.log("Player Status: SEEKING"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.COMPLETE: 
            console.log("Player Status: COMPLETE"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.RELEASED: 
            console.log("Player Status: RELEASED"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.ERROR: 
            console.log("Player Status: ERROR"); 
            break; 
    } 
};
```

