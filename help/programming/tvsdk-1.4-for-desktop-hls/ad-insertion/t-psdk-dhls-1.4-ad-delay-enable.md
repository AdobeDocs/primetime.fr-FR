---
description: Vous pouvez indiquer si la lecture doit être autorisée avant le chargement et le placement de toutes les publicités dans la chronologie. Le démarrage de la lecture de cette manière permet à la visionneuse d’accéder plus rapidement au contenu principal. Cette fonctionnalité s’applique uniquement aux enregistrements DVR en direct et ne fonctionne pas sur les ressources VOD, par exemple.
title: Activation du chargement des publicités différées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Activation du chargement des publicités différées{#enable-lazy-ad-loading}

Vous pouvez indiquer si la lecture doit être autorisée avant le chargement et le placement de toutes les publicités dans la chronologie. Le démarrage de la lecture de cette manière permet à la visionneuse d’accéder plus rapidement au contenu principal. Cette fonctionnalité s’applique uniquement aux enregistrements DVR en direct et ne fonctionne pas sur les ressources VOD, par exemple.

1. Utilisation de la propriété booléenne `delayAdLoading` in `AdvertisingMetadata`.

   * Lorsque la valeur est false, TVSDK attend que toutes les publicités soient résolues et placées avant de passer à l’état PRÉPARÉ . La valeur par défaut est false.
   * Si la valeur est true, TVSDK résout uniquement les publicités initiales et passe à l’état PRÉPARÉ . Les publicités restantes sont résolues et placées pendant la lecture.

1. Pour activer également le chargement différé de publicités avec la prise de décision publicitaire Adobe Primetime, définissez cette variable sur `true` lorsque vous créez `AuditudeSettings`.

   La variable `AuditudeSettings` hérite de cette propriété de `AdvertisingMetadata`, mais n’hérite pas de la valeur actuelle.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings(); 
   auditudeSettings.mediaId = ... 
   auditudeSettings.zoneId = ... 
   auditudeSettings.delayAdLoading = true;
   ```

1. Pour représenter précisément les publicités comme repères sur une barre de défilement, écoutez le `TimelineEvent`. `TIMELINE_UPDATED` et redessinez la barre de défilement chaque fois que vous recevez cet événement.

   Lorsque les diffusions VoD utilisent le chargement différé de la publicité, toutes les publicités ne sont pas placées dans la chronologie lorsque votre lecteur accède à l’état PRÉPARÉ. Vous devez donc redessiner explicitement la barre de défilement.

   TVSDK optimise la distribution de cet événement afin de minimiser le nombre de fois où vous devez redessiner la barre de défilement. Par conséquent, le nombre d’événements de la chronologie n’est pas lié au nombre de coupures publicitaires à placer sur la chronologie. Par exemple, si vous avez cinq coupures publicitaires, vous ne recevrez peut-être pas exactement cinq événements.

   ```
   mediaPlayer.addEventListener(TimelineEvent.TIMELINE_UPDATED, onTimelineUpdated); 
   // ... 
   function onTimelineUpdated(event:TimelineEvent):void { 
       // get markers 
       var markers:Vector.<TimelineMarker> = event.timeline.timelineMarkers; 
       drawMarkers(markers); 
   } 
   ```
