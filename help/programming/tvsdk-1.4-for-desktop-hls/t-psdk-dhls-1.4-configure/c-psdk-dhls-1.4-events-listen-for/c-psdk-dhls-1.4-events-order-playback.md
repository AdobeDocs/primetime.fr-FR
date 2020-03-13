---
description: TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.
seo-description: TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.
seo-title: 'Ordre du de lecture '
title: 'Ordre du de lecture '
uuid: 4a9ea66b-a383-46ff-9ab8-983b1dd7f935
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Ordre du de lecture{#order-of-playback-events}

TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.

<!--<a id="section_6E34A6C7936245D88DEB3315DA64598B"></a>-->

Les exemples suivants montrent l’ordre de certains  qui incluent des  de lecture.

* Lors du chargement réussi d’une ressource multimédia via `MediaPlayer.replaceCurrentResource`, l’ordre des  est le suivant :

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZING`

   * `MediaPlayerItemEvent.ITEM_CREATED`
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZED`

* Lors de la préparation de la lecture `MediaPlayer.prepareToPlay`, l’ordre des  est le suivant :

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARING`

   * `TimelineEvent.TIMELINE_UPDATED` si des publicités ont été insérées
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARED`

* Pour les flux en direct/linéaires, pendant la lecture au fur et à mesure que la fenêtre de lecture avance et que des opportunités supplémentaires sont résolues, l’ordre des  est le suivant :

   * `MediaPlayerItemEvent.ITEM_UPDATED`
   * `TimelineEvent.TIMELINE_UPDATED` si des publicités ont été insérées

<!--<a id="section_76C13548AF934868B70757CA5489E516"></a>-->

L’exemple suivant illustre une progression type des  :

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

