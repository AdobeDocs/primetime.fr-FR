---
description: TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions en fonction des événements de la séquence prévue.
seo-description: TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions en fonction des événements de la séquence prévue.
seo-title: Ordre des événements de lecture
title: Ordre des événements de lecture
uuid: 4a9ea66b-a383-46ff-9ab8-983b1dd7f935
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Ordre des événements de lecture{#order-of-playback-events}

TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions en fonction des événements de la séquence prévue.

<!--<a id="section_6E34A6C7936245D88DEB3315DA64598B"></a>-->

Les exemples suivants montrent l’ordre de certains événements incluant des événements de lecture.

* Lors du chargement réussi d&#39;une ressource multimédia par `MediaPlayer.replaceCurrentResource`l&#39;intermédiaire de, l&#39;ordre des événements est le suivant :

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZING`

   * `MediaPlayerItemEvent.ITEM_CREATED`
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZED`

* Lors de la préparation de la lecture à travers `MediaPlayer.prepareToPlay`la vidéo, l’ordre des événements est le suivant :

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARING`

   * `TimelineEvent.TIMELINE_UPDATED` si des publicités ont été insérées
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARED`

* Pour les flux en direct/linéaires, pendant la lecture, à mesure que la fenêtre de lecture avance et que des opportunités supplémentaires sont résolues, l’ordre des événements est le suivant :

   * `MediaPlayerItemEvent.ITEM_UPDATED`
   * `TimelineEvent.TIMELINE_UPDATED` si des publicités ont été insérées

<!--<a id="section_76C13548AF934868B70757CA5489E516"></a>-->

L’exemple suivant illustre une progression type des événements :

```
mediaPlayer.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
public function onItemCreated(event:MediaPlayerItemEvent):void { 
    var item:MediaPlayerItem = event.item; 
    ... 
} 
mediaPlayer.addEventListener(MediaPlayerItemEvent.ITEM_UPDATED, onItemUpdated); 
public function onItemUpdated(event:MediaPlayerItemEvent):void { 
    var item:MediaPlayerItem = event.item; 
    ... 
} 
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
public function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    switch(event.status){ 
        case MediaPlayerStatus.INITIALIZING: 
        case MediaPlayerStatus.INITIALIZED: 
        ... 
    } 
    ... 
} 
mediaPlayer.addEventListener(TimeChangeEvent.TIME_CHANGED, onTimeChanged); 
public function onTimeChanged(event:TimeChangeEvent):void { 
    var timeInMilliseconds:Number = event.time; 
    ... 
}
```

