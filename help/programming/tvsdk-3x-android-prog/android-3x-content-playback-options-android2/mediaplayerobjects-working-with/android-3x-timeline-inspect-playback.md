---
description: Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel sont identifiées les sections de contenu qui correspondent au contenu de la publicité.
seo-description: Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel sont identifiées les sections de contenu qui correspondent au contenu de la publicité.
seo-title: Vérifier la chronologie de la lecture
title: Vérifier la chronologie de la lecture
uuid: d5d68684-d658-44bc-bfff-952b7946c7fd
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Vérifier la chronologie de la lecture {#inspect-the-playback-timeline}

Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel sont identifiées les sections de contenu qui correspondent au contenu de la publicité.

Voici un exemple d’implémentation, comme le montre la capture d’écran suivante.  ![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. Accédez à l’ `Timeline` objet dans la `MediaPlayer` méthode à l’aide de la `getTimeline()` méthode.

   La `Timeline` classe encapsule les informations liées au contenu du plan de montage chronologique associé à l’élément média actuellement chargé par l’ `MediaPlayer` instance. La `Timeline` classe donne accès à un en lecture seule du plan de montage chronologique sous-jacent. La `Timeline` classe fournit une méthode getter qui fournit un itérateur à travers un d’ `TimelineMarker` objets.

1. Effectuez une itération dans le de `TimelineMarkers` et utilisez les informations renvoyées pour mettre en oeuvre votre chronologie.

       Un objet &quot;TimelineMarker&quot; contient deux informations :
   
   * Position du marqueur sur la chronologie (en millisecondes)
   * Durée du marqueur sur la chronologie (en millisecondes)

1. Prêtez attention au `MediaPlayerEvent.TIMELINE_UPDATED` sur l’ `MediaPlayer` instance et implémentez le `TimelineUpdatedEventListener.onTimelineUpdated()` rappel.

   L’ `Timeline` objet peut informer votre application des modifications qui peuvent se produire dans le plan de montage chronologique de la lecture en appelant votre `OnTimelineUpdated` écouteur.

```java
// access the timeline object 
Timeline timeline = mediaPlayer.getTimeline(); 
 
// Iterate through the list of TimelineMarkers 
Iterator<TimelineMarker> iterator = timeline.timelineMarkers(); 
 
while (iterator.hasNext()) { 
    TimelineMarker marker = iterator.next(); 
    // the start position of the marker 
    long startPos = marker.getTime(); 
    // the duration of the marker 
    long duration = marker.getDuration(); 
}
```
