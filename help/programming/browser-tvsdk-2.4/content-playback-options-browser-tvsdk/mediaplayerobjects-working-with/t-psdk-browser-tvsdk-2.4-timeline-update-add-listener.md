---
description: Pour recevoir des notifications sur les mises à jour de la chronologie, enregistrez les écouteurs de événement appropriés.
title: Ajouter des écouteurs pour TimelineUpdateEvent
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# Ajouter des écouteurs pour TimelineUpdateEvent{#add-listeners-for-timelineupdatedevent}

Pour recevoir des notifications sur les mises à jour de la chronologie, enregistrez les écouteurs de événement appropriés.

Chaque fois que la chronologie est mise à jour, le `MediaPlayer` envoie `AdobePSDK.TimelineEvent` avec le type `AdobePSDK.PSDKEventType.TIMELINE_UPDATED`.
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

1. Enregistrez les écouteurs de événement.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMELINE_UPDATED,  
       onTimelineUpdatedEvent);
   ```

