---
description: Cet exemple illustre la méthode recommandée pour inclure des spécifications de plage temporelle dans la chronologie de lecture.
title: Placez des marqueurs publicitaires de période sur la chronologie.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Placez des marqueurs publicitaires de période sur la chronologie. {#place-timerange-ad-markers-on-the-timeline}

Cet exemple illustre la méthode recommandée pour inclure des spécifications de plage temporelle dans la chronologie de lecture.

1. Traduisez les informations de positionnement des publicités hors-bande dans une liste de `TimeRange` les spécifications (c’est-à-dire les instances de la variable `TimeRange` ).
1. Utilisez le jeu de `TimeRange` spécifications pour renseigner une instance de la variable `TimeRangeCollection` classe .
1. Transmettez l’instance de métadonnées, qui peut être obtenue à partir de la méthode `TimeRangeCollection` à l’instance `replaceCurrentItem` (partie intégrante de la méthode `MediaPlayer` ).
1. Attendez que TVSDK passe à l’état PRÉPARÉ en attendant le délai `PlaybackEventListener#onPrepared` rappel à déclencher.
1. Commencez la lecture vidéo en appelant la fonction `play()` (partie intégrante de la méthode `MediaPlayer` ).

* Gestion des conflits de chronologie : il peut arriver que certains `TimeRange` chevauchement des spécifications sur la chronologie de lecture. Par exemple, la valeur de la position de départ correspondant à un `TimeRange` La spécification peut être inférieure à la valeur de la position de fin déjà placée. Dans ce cas, TVSDK ajuste silencieusement la position de départ de l’offensant. `TimeRange` pour éviter les conflits de chronologie. Grâce à cet ajustement, la nouvelle `TimeRange` est plus court que celui spécifié initialement. Si l&#39;ajustement est si extrême qu&#39;il conduirait à une `TimeRange` avec une durée de zéro ms, TVSDK supprime l’offense en silence. `TimeRange` spécification.

* When `TimeRange` les spécifications des coupures publicitaires personnalisées sont fournies, TVSDK tente de les traduire en publicités regroupées dans des coupures publicitaires. TVSDK recherche les éléments adjacents `TimeRange` les spécifications et les regroupent dans des coupures publicitaires distinctes. Si des plages temporelles ne sont adjacentes à aucune autre plage horaire, elles sont converties en coupures publicitaires contenant une seule publicité.

* On suppose que l’élément du lecteur multimédia en cours de chargement pointe vers une ressource VOD. TVSDK le vérifie chaque fois que l’application tente de charger une ressource multimédia dont les métadonnées contiennent `TimeRange` les spécifications qui ne peuvent être utilisées que dans le contexte de la fonctionnalité de marqueurs d’annonce personnalisés. Si la ressource sous-jacente n’est pas de type VOD, la bibliothèque TVSDK renvoie une exception.

* Lorsque vous gérez des marqueurs publicitaires personnalisés, TVSDK désactive d’autres mécanismes de résolution des publicités (par le biais d’Adobe Primetime Ad Decisioning (précédemment connu sous le nom d’Auditude) ou d’un autre système d’approvisionnement des publicités). Vous pouvez utiliser l’un des différents modules de résolveur de publicités fournis par TVSDK ou le mécanisme de marqueurs de publicités personnalisés. Lors de l’utilisation de l’API des marqueurs d’annonce personnalisés, le contenu de la publicité est considéré comme déjà résolu et placé dans la chronologie.

<!--<a id="example_639BD1B66CE74F3DB65ED06CAD23EB09"></a>-->

Le fragment de code suivant fournit un exemple simple où un ensemble de trois `TimeRange` les spécifications sont placées sur la chronologie en tant que marqueurs publicitaires personnalisés.

```
// Assume that the 3 timerange specs are obtained through external means: CMS, etc. 
// Use these 3 timerange specs to populate the TimeRangeCollection instance 
var timeRanges:TimeRangeCollection = new TimeRangeCollection(); 
timeRanges.addTimeRange(new TimeRange(0,10000)); 
timeRanges.addTimeRange(new TimeRange(15000,20000)); 
timeRanges.addTimeRange(new TimeRange(25000,30000)); 
  
// create and configure a MediaResource instance 
MediaResource mediaResource =  
  MediaResource.createFromUrl("www.example.com/video/test_video.m3u8",  
                             timeRanges.toMetadata(null));
```
