---
description: Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné lu par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel les sections de contenu correspondant au contenu publicitaire sont identifiées.
seo-description: Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné lu par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel les sections de contenu correspondant au contenu publicitaire sont identifiées.
seo-title: Inspect de la chronologie de la lecture
title: Inspect de la chronologie de la lecture
uuid: d5d68684-d658-44bc-bfff-952b7946c7fd
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Inspect de la chronologie de la lecture {#inspect-the-playback-timeline}

Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné lu par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel les sections de contenu correspondant au contenu publicitaire sont identifiées.

Voici un exemple d’implémentation, comme illustré dans la capture d’écran suivante.  ![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. Accédez à l&#39;objet `Timeline` dans `MediaPlayer` à l&#39;aide de la méthode `getTimeline()`.

   La classe `Timeline` encapsule les informations liées au contenu de la chronologie associée à l&#39;élément média actuellement chargé par l&#39;instance `MediaPlayer`. La classe `Timeline` permet d&#39;accéder à une vue en lecture seule de la chronologie sous-jacente. La classe `Timeline` fournit une méthode getter qui fournit un itérateur via une liste d&#39;objets `TimelineMarker`.

1. Effectuez une itération à la liste de `TimelineMarkers` et utilisez les informations renvoyées pour mettre en oeuvre votre chronologie.

       Un objet &quot;TimelineMarker&quot; contient deux informations :
   
   * Position du marqueur sur la chronologie (en millisecondes)
   * Durée du marqueur sur la chronologie (en millisecondes)

1. Prêtez attention au événement `MediaPlayerEvent.TIMELINE_UPDATED` sur l&#39;instance `MediaPlayer` et implémentez le rappel `TimelineUpdatedEventListener.onTimelineUpdated()`.

   L&#39;objet `Timeline` peut informer votre application des modifications qui peuvent se produire dans le plan de montage chronologique de lecture en appelant votre écouteur `OnTimelineUpdated`.

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
