---
description: Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel sont identifiées les sections de contenu qui correspondent au contenu de la publicité.
seo-description: Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel sont identifiées les sections de contenu qui correspondent au contenu de la publicité.
seo-title: Vérifier la chronologie de la lecture
title: Vérifier la chronologie de la lecture
uuid: 2f903493-2d88-4af2-ac71-36300b49735b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Vérifier la chronologie de la lecture{#inspect-the-playback-timeline}

Vous pouvez obtenir une description de la chronologie associée à l’élément actuellement sélectionné en cours de lecture par TVSDK. Cela s’avère particulièrement utile lorsque votre application affiche un contrôle de barre de défilement personnalisée dans lequel sont identifiées les sections de contenu qui correspondent au contenu de la publicité.

Voici un exemple d’implémentation, comme le montre la capture d’écran suivante.
<!--<a id="fig_6D9FB3764F3947A38B8E7726187BD461"></a>-->

![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. Accédez à l’ `Timeline` objet dans la `MediaPlayer` méthode à l’aide de la `get` méthode.

   La `Timeline` classe encapsule les informations liées au contenu du plan de montage chronologique associé à l’élément média actuellement chargé par l’ `MediaPlayer` instance. La `Timeline` classe donne accès à un en lecture seule du plan de montage chronologique sous-jacent. La `Timeline` classe fournit une méthode getter pour obtenir tous les `TimelineMarker` objets placés.

1. Effectuez une itération dans le de `TimelineMarkers` et utilisez les informations renvoyées pour mettre en oeuvre votre chronologie.

       Un objet &quot;TimelineMarker&quot; contient deux informations :
   
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

