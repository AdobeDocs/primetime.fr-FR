---
description: Pour recevoir des notifications sur les mises à jour de la chronologie, enregistrez les écouteurs d’événement appropriés.
title: Ajout d’écouteurs pour TimelineUpdatedEvent
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# Ajout d’écouteurs pour TimelineUpdatedEvent{#add-listeners-for-timelineupdatedevent}

Pour recevoir des notifications sur les mises à jour de la chronologie, enregistrez les écouteurs d’événement appropriés.

Chaque fois que la chronologie est mise à jour, la variable `MediaPlayer` dispatches `AdobePSDK.TimelineEvent` avec type `AdobePSDK.PSDKEventType.TIMELINE_UPDATED`.
1. Mettez en oeuvre les écouteurs appropriés.

   ```js
   function onTimelineUpdatedEvent(event) { 
       var timelineMarkers = event.timeline.timelineMarkers; 
       //add code to remove old timeline markers from scrub-bar. 
       var range = player.playbackRange; 
       //iterate through the list of timelineMarkers 
       for(var i = 0; i < timelineMarkers.length; i++) 
       { 
           var markerLocalTime = timelineMarkers[i].localRange.begin; 
           var markerVirtualTime = timelineMarkers[i].virtualRange.begin; 
           var duration = timelineMarkers[i].duration; 
        // add code to draw a particular marker on scrub-bar 
       }      
   }
   ```

1. Enregistrez les écouteurs d’événement.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMELINE_UPDATED,  
       onTimelineUpdatedEvent);
   ```
