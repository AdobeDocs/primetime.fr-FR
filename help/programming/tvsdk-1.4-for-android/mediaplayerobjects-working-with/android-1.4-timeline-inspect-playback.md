---
description: Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche une barre de défilement personnalisée dans laquelle les sections de contenu qui correspondent au contenu publicitaire sont identifiées.
title: Inspect de la chronologie de lecture
exl-id: af373f1e-ed5b-40a9-a91e-9eb0e4a181de
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Inspect de la chronologie de lecture{#inspect-the-playback-timeline}

Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche une barre de défilement personnalisée dans laquelle les sections de contenu qui correspondent au contenu publicitaire sont identifiées.

Voici un exemple de mise en oeuvre, comme illustré dans la capture d’écran suivante.  ![](assets/inspect-playback.jpg){width="368.641pt"}

1. Accédez au `Timeline` dans le `MediaPlayer` en utilisant la variable `getTimeline` .

   Le `Timeline` encapsule les informations liées au contenu de la chronologie associée à l’élément multimédia actuellement chargé par la variable `MediaPlayer` instance. Le `Timeline` permet d’accéder à une vue en lecture seule de la chronologie sous-jacente. Le `Timeline` fournit une méthode getter qui fournit un itérateur via une liste de `TimelineMarker` objets.

1. Parcourir la liste de `TimelineMarkers` et utilisez les informations renvoyées pour mettre en oeuvre votre chronologie.

       Un objet &quot;TimelineMarker&quot; contient deux éléments d’informations :
   
   * Position du marqueur sur la chronologie (en millisecondes)
   * Durée du marqueur sur la chronologie (en millisecondes)

1. Mise en oeuvre de l’interface de rappel des écouteurs `MediaPlayer.PlaybackEventListener.onTimelineUpdated` et l’enregistrer auprès de la fonction `Timeline` .

   Le `Timeline` peut informer votre application des modifications qui peuvent se produire dans la chronologie de lecture en appelant votre `OnTimelineUpdated` écouteur.

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
