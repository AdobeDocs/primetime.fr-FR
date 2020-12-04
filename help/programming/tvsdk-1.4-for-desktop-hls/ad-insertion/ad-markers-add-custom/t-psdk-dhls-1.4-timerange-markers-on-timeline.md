---
description: Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans la chronologie de la lecture.
seo-description: Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans la chronologie de la lecture.
seo-title: Placer des marqueurs publicitaires de la plage de temps sur le plan de montage chronologique
title: Placer des marqueurs publicitaires de la plage de temps sur le plan de montage chronologique
uuid: cbcc4c84-0d56-4331-b555-b8e59f7d52d4
translation-type: tm+mt
source-git-commit: fd21a29bb186238142d43e0277bbf92f8406f6f7
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---


# Placez des marques publicitaires TimeRange sur la chronologie {#place-timerange-ad-markers-on-the-timeline}

Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans la chronologie de la lecture.

1. Traduisez les informations de positionnement publicitaire out-of-band dans une liste de `TimeRange` spécifications (c&#39;est-à-dire les instances de la classe `TimeRange`).
1. Utilisez l&#39;ensemble de spécifications `TimeRange` pour renseigner une instance de la classe `TimeRangeCollection`.
1. Transférez l’instance de métadonnées, qui peut être obtenue de l’instance `TimeRangeCollection`, à la méthode `replaceCurrentItem` (partie de l’interface `MediaPlayer`).
1. Attendez que TVSDK soit transition à l’état PRÉPARÉ en attendant que le rappel `PlaybackEventListener#onPrepared` soit déclenché.
1. Début de la lecture vidéo en appelant la méthode `play()` (qui fait partie de l&#39;interface `MediaPlayer`).

* Gestion des conflits de chronologie : Il peut arriver que certaines spécifications `TimeRange` se chevauchent sur la chronologie de la lecture. Par exemple, la valeur de la position du début correspondant à une spécification `TimeRange` peut être inférieure à la valeur de la position de fin déjà placée. Dans ce cas, TVSDK ajuste en silence la position début de la spécification `TimeRange` incriminée afin d’éviter les conflits de chronologie. Grâce à cet ajustement, le nouveau `TimeRange` devient plus court que celui spécifié initialement. Si l’ajustement est si extrême qu’il conduirait à un `TimeRange` d’une durée de zéro ms, TVSDK supprime en silence la spécification `TimeRange` incriminée.

* Lorsque des `TimeRange` spécifications pour les coupures publicitaires personnalisées sont fournies, TVSDK tente de les traduire en publicités regroupées dans des coupures publicitaires. TVSDK recherche les spécifications `TimeRange` adjacentes et les regroupe en pauses publicitaires distinctes. S’il existe des plages de temps qui ne sont adjacentes à aucune autre plage de temps, elles sont traduites en coupures publicitaires contenant une seule publicité.

* On suppose que l’élément du lecteur multimédia en cours de chargement pointe vers une ressource VOD. TVSDK le vérifie chaque fois que votre application tente de charger une ressource multimédia dont les métadonnées contiennent des spécifications `TimeRange` qui ne peuvent être utilisées que dans le contexte de la fonctionnalité de marques publicitaires personnalisées. Si la ressource sous-jacente n’est pas de type VOD, la bibliothèque TVSDK renvoie une exception.

* Lorsqu’il s’agit de marques publicitaires personnalisées, TVSDK désactive d’autres mécanismes de résolution de publicités (par le biais de la prise de décision d’annonce Adobe Primetime (précédemment connue sous le nom d’Auditude) ou d’un autre système d’approvisionnement d’annonce). Vous pouvez utiliser l’un des divers modules de résolution d’annonces fournis par TVSDK ou le mécanisme de balisage publicitaire personnalisé. Lors de l’utilisation de l’API des marqueurs publicitaires personnalisés, le contenu de la publicité est considéré comme déjà résolu et placé sur la chronologie.

<!--<a id="example_639BD1B66CE74F3DB65ED06CAD23EB09"></a>-->

Le fragment de code suivant fournit un exemple simple où un ensemble de trois spécifications `TimeRange` est placé sur le plan de montage chronologique en tant que marques publicitaires personnalisées.

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
