---
description: Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans le plan de montage chronologique de la lecture.
seo-description: Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans le plan de montage chronologique de la lecture.
seo-title: Placer des marqueurs publicitaires de la période sur le plan de montage chronologique
title: Placer des marqueurs publicitaires de la période sur le plan de montage chronologique
uuid: cbcc4c84-0d56-4331-b555-b8e59f7d52d4
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Placer des marqueurs publicitaires de la période sur le plan de montage chronologique {#place-timerange-ad-markers-on-the-timeline}

Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans le plan de montage chronologique de la lecture.

1. Traduisez les informations de positionnement publicitaire hors bande dans un de `TimeRange` spécifications (c’est-à-dire les instances de la `TimeRange` classe).
1. Utilisez l’ensemble de `TimeRange` spécifications pour renseigner une instance de la `TimeRangeCollection` classe.
1. Transmettez l’instance de métadonnées, qui peut être obtenue à partir de l’ `TimeRangeCollection` instance, à la `replaceCurrentItem` méthode (partie de l’ `MediaPlayer` interface).
1. Attendez que TVSDK soit  à l’état PRÉPARÉ en attendant que le rappel soit déclenché. `PlaybackEventListener#onPrepared`
1. de la lecture vidéo en appelant la `play()` méthode (partie de l’ `MediaPlayer` interface).

* Gestion des conflits de chronologie : Il peut arriver que certaines `TimeRange` spécifications se chevauchent sur le plan de temps de lecture. Par exemple, la valeur de la position  du correspondant à une `TimeRange` spécification peut être inférieure à la valeur de la position de fin déjà placée. Dans ce cas, TVSDK ajuste en silence la position  de la spécification incriminée afin d’éviter les conflits de chronologie. `TimeRange` Grâce à cet ajustement, le nouveau `TimeRange` devient plus court que celui initialement spécifié. Si l&#39;ajustement est si extrême qu&#39;il conduirait à un `TimeRange` avec une durée de zéro ms, TVSDK abandonne silencieusement la `TimeRange` spécification offensante.

* Lorsque `TimeRange` des spécifications pour les coupures publicitaires personnalisées sont fournies, TVSDK tente de les traduire en publicités regroupées dans des coupures publicitaires. TVSDK recherche les `TimeRange` spécifications adjacentes et les regroupe dans des pauses publicitaires distinctes. S’il existe des plages temporelles qui ne sont adjacentes à aucune autre plage temporelle, elles sont converties en pauses publicitaires contenant une seule publicité.

* On suppose que l’élément du lecteur multimédia en cours de chargement pointe vers une ressource VOD. TVSDK vérifie cette information chaque fois que l’application tente de charger une ressource multimédia dont les métadonnées contiennent `TimeRange` des spécifications qui ne peuvent être utilisées que dans le contexte de la fonctionnalité de marques publicitaires personnalisées. Si la ressource sous-jacente n’est pas de type VOD, la bibliothèque TVSDK renvoie une exception.

* Lorsqu’il est question de marques publicitaires personnalisées, TVSDK désactive d’autres mécanismes de résolution des publicités (par le biais d’Adobe Primetime et de la prise de décision publicitaire (précédemment connue sous le nom d’Auditude) ou d’un autre système d’attribution de privilèges d’accès aux publicités). Vous pouvez utiliser l’un des différents modules de résolution d’annonces fournis par TVSDK ou le mécanisme de balisage d’annonces personnalisé. Lors de l’utilisation de l’API des marqueurs publicitaires personnalisés, le contenu de la publicité est considéré comme déjà résolu et placé sur le plan de montage chronologique.
>
><!--<a id="example_639BD1B66CE74F3DB65ED06CAD23EB09"></a>-->


Le fragment de code suivant fournit un exemple simple où un ensemble de trois `TimeRange` spécifications est placé sur le plan de montage chronologique sous forme de marqueurs publicitaires personnalisés.

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
