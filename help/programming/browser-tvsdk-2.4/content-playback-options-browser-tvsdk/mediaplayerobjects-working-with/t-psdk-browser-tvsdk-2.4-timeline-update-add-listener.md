---
description: Pour recevoir des notifications sur les mises à jour de la chronologie, enregistrez les écouteurs de événement appropriés.
seo-description: Pour recevoir des notifications sur les mises à jour de la chronologie, enregistrez les écouteurs de événement appropriés.
seo-title: Ajouter des écouteurs pour TimelineUpdateEvent
title: Ajouter des écouteurs pour TimelineUpdateEvent
uuid: 7d742e15-5a55-4155-93a7-7b79f21c1472
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '62'
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

