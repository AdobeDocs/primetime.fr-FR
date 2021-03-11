---
description: Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans la chronologie de la lecture.
title: Placer des marqueurs publicitaires de la plage de temps sur le plan de montage chronologique
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Placez des marques publicitaires TimeRange sur la chronologie {#place-timerange-ad-markers-on-the-timeline}

Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans la chronologie de la lecture.

1. Traduisez les informations de positionnement publicitaire out-of-band dans une liste de `TimeRange` spécifications (c&#39;est-à-dire les instances de la classe `TimeRange`).
1. Utilisez l&#39;ensemble de spécifications `TimeRange` pour renseigner une instance de la classe `TimeRangeCollection`.
1. Transférez l’instance de métadonnées, qui peut être obtenue de l’instance `TimeRangeCollection`, à la méthode `replaceCurrentItem` (qui fait partie de l’interface de MediaPlayer).
1. Attendez que TVSDK soit transition à l’état `PREPARED` en attendant que le rappel `PlaybackEventListener#onPrepared` soit déclenché.
1. Début de la lecture vidéo en appelant la méthode `play()` (qui fait partie de l&#39;interface `MediaPlayer`).

* Gestion des conflits de chronologie : Il peut arriver que certaines spécifications `TimeRange` se chevauchent sur la chronologie de la lecture. Par exemple, la valeur de la position du début correspondant à une spécification `TimeRange` peut être inférieure à la valeur de la position de fin déjà placée. Dans ce cas, TVSDK ajuste en silence la position début de la spécification `TimeRange` incriminée afin d’éviter les conflits de chronologie. Grâce à cet ajustement, le nouveau `TimeRange` devient plus court que celui spécifié initialement. Si l’ajustement est si extrême qu’il conduirait à un `TimeRange` d’une durée de zéro ms, TVSDK supprime en silence la spécification `TimeRange` incriminée.
* Lorsque des `TimeRange` spécifications pour les coupures publicitaires personnalisées sont fournies, TVSDK tente de les traduire en publicités regroupées dans des coupures publicitaires. TVSDK recherche les spécifications `TimeRange` adjacentes et les regroupe en pauses publicitaires distinctes. S’il existe des plages de temps qui ne sont adjacentes à aucune autre plage de temps, elles sont traduites en coupures publicitaires contenant une seule publicité.
* On suppose que l’élément du lecteur multimédia en cours de chargement pointe vers une ressource VOD. TVSDK le vérifie chaque fois que votre application tente de charger une ressource multimédia dont les métadonnées contiennent des spécifications `TimeRange` qui ne peuvent être utilisées que dans le contexte de la fonctionnalité de marques publicitaires personnalisées. Si la ressource sous-jacente n’est pas de type VOD, la bibliothèque TVSDK renvoie une exception.
* Lorsqu’il s’agit de marques publicitaires personnalisées, TVSDK désactive d’autres mécanismes de résolution de publicités (par le biais de la prise de décision d’annonce Adobe Primetime (précédemment connue sous le nom d’Auditude) ou d’un autre système d’approvisionnement d’annonce). Vous pouvez utiliser l’un des divers modules de résolution d’annonces fournis par TVSDK ou le mécanisme de balisage publicitaire personnalisé. Lors de l’utilisation de l’API des marqueurs publicitaires personnalisés, le contenu de la publicité est considéré comme déjà résolu et placé sur la chronologie.

Le fragment de code suivant fournit un exemple simple dans lequel un ensemble de trois spécifications TimeRange sont placées sur le plan de montage chronologique en tant que marques publicitaires personnalisées.

```java>
// Assume that the 3 timerange specs are obtained through external means: CMS, etc. 
// Use these 3 timerange specs to populate the TimeRangeCollection instance 
TimeRangeCollection timeRanges = new TimeRangeCollection();  
timeRanges.addTimeRange(new TimeRange(0,10000)); 
timeRanges.addTimeRange(new TimeRange(15000,20000)); 
timeRanges.addTimeRange(new TimeRange(25000,30000)); 
 
// create and configure a MediaResource instance 
MediaResource mediaResource =  
  MediaResource.createFromUrl("www.example.com/video/test_video.m3u8",  
                               timeRanges.toMetadata(null)); 
 
// prepare the content for playback by creating 
// NOTE: mediaPlayer is an instance of a properly configured MediaPlayer  
mediaPlayer.replaceCurrentItem(mediaResource); 
// wait for TVSDK to reach the PREPARED state 
... 
MediaPlayer.PlaybackEventListener playbackEventListener = new 
  MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // TVSDK in in the PREPARED state. We are allowed to start the playback  
        mediaPlayer.play(); 
    } 
} 
```
