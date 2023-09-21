---
description: TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence attendue.
title: Ordre des événements de lecture
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Ordre des événements de lecture{#order-of-playback-events}

TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence attendue.

<!--<a id="section_6E34A6C7936245D88DEB3315DA64598B"></a>-->

Les exemples suivants montrent l’ordre de certains événements qui incluent des événements de lecture.

* Lors du chargement réussi d’une ressource multimédia via `MediaPlayer.replaceCurrentResource`, l’ordre des événements est le suivant :

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZING`

   * `MediaPlayerItemEvent.ITEM_CREATED`
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZED`

* Lors de la préparation de la lecture `MediaPlayer.prepareToPlay`, l’ordre des événements est le suivant :

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARING`

   * `TimelineEvent.TIMELINE_UPDATED` si des publicités ont été insérées ;
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARED`

* Pour les flux en direct/linéaires, pendant la lecture lorsque la fenêtre de lecture avance et que des opportunités supplémentaires sont résolues, l’ordre des événements est le suivant :

   * `MediaPlayerItemEvent.ITEM_UPDATED`
   * `TimelineEvent.TIMELINE_UPDATED` si des publicités ont été insérées ;

<!--<a id="section_76C13548AF934868B70757CA5489E516"></a>-->

L’exemple suivant illustre une progression type d’événements :

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
