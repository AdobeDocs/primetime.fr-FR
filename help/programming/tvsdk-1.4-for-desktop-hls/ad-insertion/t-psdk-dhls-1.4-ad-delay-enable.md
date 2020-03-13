---
description: Vous pouvez indiquer si la lecture doit être autorisée avant que toutes les publicités ne soient chargées et placées dans le plan de montage chronologique. Le démarrage de la lecture de cette manière permet à un lecteur d’accéder plus rapidement au contenu principal. Cette fonctionnalité s’applique uniquement aux magnétoscopes en direct et ne fonctionne pas, par exemple, sur les ressources VOD.
seo-description: Vous pouvez indiquer si la lecture doit être autorisée avant que toutes les publicités ne soient chargées et placées dans le plan de montage chronologique. Le démarrage de la lecture de cette manière permet à un lecteur d’accéder plus rapidement au contenu principal. Cette fonctionnalité s’applique uniquement aux magnétoscopes en direct et ne fonctionne pas, par exemple, sur les ressources VOD.
seo-title: Activer le chargement différé des publicités
title: Activer le chargement différé des publicités
uuid: ac7c8801-7fa2-4f17-b79c-c603b3236948
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Activer le chargement différé des publicités{#enable-lazy-ad-loading}

Vous pouvez indiquer si la lecture doit être autorisée avant que toutes les publicités ne soient chargées et placées dans le plan de montage chronologique. Le démarrage de la lecture de cette manière permet à un lecteur d’accéder plus rapidement au contenu principal. Cette fonctionnalité s’applique uniquement aux magnétoscopes en direct et ne fonctionne pas, par exemple, sur les ressources VOD.

1. Utilisez la propriété booléenne `delayAdLoading` dans `AdvertisingMetadata`.

   * Lorsque la valeur est false, TVSDK attend que toutes les publicités soient résolues et placées avant de passer à l’état PRÉPARÉ. Elle est définie sur false par défaut.
   * Lorsque la valeur est true, TVSDK résout uniquement les publicités et les  initiaux sur l’état PRÉPARÉ. Les publicités restantes sont résolues et placées pendant la lecture.

1. Pour activer également le chargement différé des publicités avec la prise de décision publicitaire Adobe Primetime, définissez cette option sur `true` au moment de la création `AuditudeSettings`.

   La `AuditudeSettings` classe hérite de cette propriété de `AdvertisingMetadata`, mais n’hérite pas de la valeur actuelle.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings(); 
   auditudeSettings.mediaId = ... 
   auditudeSettings.zoneId = ... 
   auditudeSettings.delayAdLoading = true;
   ```

1. Pour représenter précisément les publicités comme des indices sur une barre de défilement, écoutez le `TimelineEvent`. `TIMELINE_UPDATED`  et redessinez la barre de défilement chaque fois que vous recevez ce .

   Lorsque les flux VoD utilisent le chargement différé des publicités, toutes les publicités ne sont pas placées dans le plan de montage chronologique lorsque votre lecteur entre dans l’état PRÉPARÉ. Vous devez donc redessiner explicitement la barre de défilement.

   TVSDK optimise l’envoi de ce pour minimiser le nombre de fois où vous devez redessiner la barre de défilement ; par conséquent, le nombre de  de la chronologie n’est pas lié au nombre de coupures publicitaires à placer sur la chronologie. Par exemple, si vous avez cinq coupures publicitaires, vous ne recevrez peut-être pas exactement cinq .

   ```
   mediaPlayer.addEventListener(TimelineEvent.TIMELINE_UPDATED, onTimelineUpdated); 
   // ... 
   function onTimelineUpdated(event:TimelineEvent):void { 
       // get markers 
       var markers:Vector.<TimelineMarker> = event.timeline.timelineMarkers; 
       drawMarkers(markers); 
   } 
   ```

