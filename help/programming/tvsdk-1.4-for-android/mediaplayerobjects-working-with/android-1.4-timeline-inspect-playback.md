---
description: Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel sont identifiées les sections de contenu qui correspondent au contenu de la publicité.
seo-description: Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel sont identifiées les sections de contenu qui correspondent au contenu de la publicité.
seo-title: Vérifier la chronologie de la lecture
title: Vérifier la chronologie de la lecture
uuid: b5ede131-1037-449b-bc3f-a066fdc92fc5
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Vérifier la chronologie de la lecture{#inspect-the-playback-timeline}

Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel sont identifiées les sections de contenu qui correspondent au contenu de la publicité.

Voici un exemple d’implémentation, comme le montre la capture d’écran suivante.  ![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. Accédez à l’ `Timeline` objet dans la `MediaPlayer` méthode à l’aide de la `getTimeline` méthode.

   La `Timeline` classe encapsule les informations liées au contenu du plan de montage chronologique associé à l’élément média actuellement chargé par l’ `MediaPlayer` instance. La `Timeline` classe donne accès à un en lecture seule du plan de montage chronologique sous-jacent. La `Timeline` classe fournit une méthode getter qui fournit un itérateur à travers un d’ `TimelineMarker` objets.

1. Effectuez une itération dans le de `TimelineMarkers` et utilisez les informations renvoyées pour mettre en oeuvre votre chronologie.

       Un objet &quot;TimelineMarker&quot; contient deux informations :
   
   * Position du marqueur sur la chronologie (en millisecondes)
   * Durée du marqueur sur la chronologie (en millisecondes)

1. Implémentez l’interface de rappel du module d’écoute `MediaPlayer.PlaybackEventListener.onTimelineUpdated` et enregistrez-la avec l’ `Timeline` objet.

   L’ `Timeline` objet peut informer votre application des modifications qui peuvent se produire dans le plan de montage chronologique de la lecture en appelant votre `OnTimelineUpdated` écouteur.

```java
// access the timeline object 
Timeline timeline = mediaPlayer.getTimeline(); 
// iterate through the list of TimelineMarkers 
Iterator<TimelineMarker> iterator = timeline.timelineMarkers(); 
while (iterator.hasNext()) { 
   TimelineMarker marker = iterator.next(); 
   // the start position of the marker 
   long startPos = marker.getTime(); 
   // the duration of the marker 
   long duration = marker.getDuration(); 
}
```

