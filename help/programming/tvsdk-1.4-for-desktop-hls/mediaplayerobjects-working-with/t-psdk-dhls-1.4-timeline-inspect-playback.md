---
description: Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche une barre de défilement personnalisée dans laquelle les sections de contenu qui correspondent au contenu publicitaire sont identifiées.
title: Inspect de la chronologie de lecture
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Inspect de la chronologie de lecture{#inspect-the-playback-timeline}

Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche une barre de défilement personnalisée dans laquelle les sections de contenu qui correspondent au contenu publicitaire sont identifiées.

Voici un exemple de mise en oeuvre, comme illustré dans la capture d’écran suivante.
<!--<a id="fig_6D9FB3764F3947A38B8E7726187BD461"></a>-->

![](assets/inspect-playback.jpg){width="368.641pt"}

1. Accédez au `Timeline` dans le `MediaPlayer` en utilisant la variable `get` .

   La variable `Timeline` encapsule les informations liées au contenu de la chronologie associée à l’élément multimédia actuellement chargé par la variable `MediaPlayer` instance. La variable `Timeline` permet d’accéder à une vue en lecture seule de la chronologie sous-jacente. La variable `Timeline` fournit une méthode getter pour obtenir tous les éléments placés `TimelineMarker` objets.

1. Parcourir la liste de `TimelineMarkers` et utilisez les informations renvoyées pour mettre en oeuvre votre chronologie.

       Un objet &quot;TimelineMarker&quot; contient deux éléments d’informations :
   
   * Position du marqueur sur la chronologie (en millisecondes)
   * Durée du marqueur sur la chronologie (en millisecondes)

<!--<a id="example_BA936629E82B4082A2E2C548E3FC3357"></a>-->

```
// access the timeline object 
var timeline:Timeline = mediaPlayer.timeline; 
 
// iterate through the list of TimelineMarkers 
var markers:Vector.<TimelineMarker> = timeline.timelineMarkers; 
markers.forEach(function(item:TimelineMarker,  
                         index:int,  
                         vector:Vector.<TimelineMarker>):void { 
    
    // the start position of the marker 
    var startPos:Number = item.time; 
 
    // the duration of the marker 
    var duration:Number = item.duration; 
 
    // draw the marker on the scrub-bar 
}
```
