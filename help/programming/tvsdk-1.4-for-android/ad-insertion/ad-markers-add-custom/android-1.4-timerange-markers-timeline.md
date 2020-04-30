---
description: Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans la chronologie de la lecture.
seo-description: Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans la chronologie de la lecture.
seo-title: Placer des marqueurs publicitaires de la plage de temps sur le plan de montage chronologique
title: Placer des marqueurs publicitaires de la plage de temps sur le plan de montage chronologique
uuid: 12935eba-2e91-40ea-a60e-02d0060c3cce
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Placer des marqueurs publicitaires de la plage de temps sur le plan de montage chronologique {#place-timerange-ad-markers-on-the-timeline}

Cet exemple montre la méthode recommandée pour inclure des spécifications TimeRange dans la chronologie de la lecture.

1. Traduisez les informations de positionnement publicitaire out-of-band dans une liste de `TimeRange` spécifications (c’est-à-dire les instances de la `TimeRange` classe).
1. Utilisez l&#39;ensemble de `TimeRange` spécifications pour renseigner une instance de la `TimeRangeCollection` classe.
1. Transférez l’instance de métadonnées, qui peut être obtenue à partir de l’ `TimeRangeCollection` instance, à la `replaceCurrentItem` méthode (partie de l’interface de MediaPlayer).
1. Attendez que TVSDK soit transition à l’ `PREPARED` état en attendant que le rappel `PlaybackEventListener#onPrepared` soit déclenché.
1. Début de la lecture vidéo en appelant la `play()` méthode (partie de l’ `MediaPlayer` interface).

* Gestion des conflits de chronologie : Il peut arriver que certaines `TimeRange` spécifications se chevauchent sur la chronologie de la lecture. Par exemple, la valeur de la position du début correspondant à une `TimeRange` spécification peut être inférieure à la valeur de la position de fin déjà placée. Dans ce cas, TVSDK ajuste en silence la position début de la spécification incriminée `TimeRange` pour éviter les conflits de chronologie. Grâce à cet ajustement, le nouveau `TimeRange` est plus court que celui qui a été initialement spécifié. Si l&#39;ajustement est si extrême qu&#39;il conduirait à un `TimeRange` avec une durée de zéro ms, TVSDK abandonne silencieusement la `TimeRange` spécification incriminée.
* Lorsque `TimeRange` des spécifications pour les coupures publicitaires personnalisées sont fournies, TVSDK tente de les traduire en publicités regroupées dans des coupures publicitaires. TVSDK recherche les spécifications adjacentes `TimeRange` et les regroupe dans des coupures publicitaires distinctes. S’il existe des plages de temps qui ne sont adjacentes à aucune autre plage de temps, elles sont traduites en coupures publicitaires contenant une seule publicité.
* On suppose que l’élément du lecteur multimédia en cours de chargement pointe vers une ressource VOD. TVSDK le vérifie chaque fois que votre application tente de charger une ressource multimédia dont les métadonnées contiennent `TimeRange` des spécifications qui peuvent être utilisées uniquement dans le contexte de la fonction de marques publicitaires personnalisées. Si la ressource sous-jacente n’est pas de type VOD, la bibliothèque TVSDK renvoie une exception.
* Lorsqu’il s’agit de marques publicitaires personnalisées, TVSDK désactive d’autres mécanismes de résolution de publicités (par le biais de la prise de décision publicitaire Adobe Primetime (précédemment connue sous le nom d’Auditude) ou d’un autre système d’approvisionnement publicitaire). Vous pouvez utiliser l’un des divers modules de résolution d’annonces fournis par TVSDK ou le mécanisme de balisage publicitaire personnalisé. Lors de l’utilisation de l’API des marqueurs publicitaires personnalisés, le contenu de la publicité est considéré comme déjà résolu et placé sur la chronologie.

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
