---
description: MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
title: Chargement d'une ressource multimédia à l'aide de MediaPlayerItemLoader
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 1%

---


# Charger une ressource multimédia à l’aide de MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader}

MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.

Par l&#39;intermédiaire de la classe `MediaPlayerItemLoader`, vous pouvez échanger une ressource média pour le `MediaPlayerItem` correspondant sans attacher une vue à une instance `MediaPlayer`, ce qui conduirait à l&#39;allocation des ressources matérielles de décodage vidéo. Le processus d&#39;obtention de l&#39;instance `MediaPlayerItem` est asynchrone.

1. Mettez en oeuvre des écouteurs de événement pour ces `MediaPlayerItemLoader` événements :

   * `MediaPlayerItemLoaderEvent.ERROR` événement

      TVSDK l’utilise pour informer votre application qu’une erreur s’est produite. TVSDK fournit une propriété d’erreur qui contient des informations de diagnostic.

1. Enregistrez cette instance dans le `MediaPlayerItemLoader`.
1. Appelez `DefaultMediaPlayerItemLoader.load`, en transmettant une instance d&#39;un objet `MediaResource`.

   L&#39;URL de l&#39;objet `MediaResource` doit pointer vers le flux pour lequel vous souhaitez obtenir des informations. Par exemple :

   ```
   private function onLoadError(event:MediaPlayerItemLoaderEvent):void { 
       // something went wrong - look at the error code and description 
       // contained within the event.error 
   } 
   private function onLoadCompleted(event:MediaPlayerItemLoaderEvent):void { 
       // information is available - look at the data in the "event.item" object 
   } 
   // instantiate the MediaPlayerItemLoader object and register event listeners 
   var itemLoader:MediaPlayerItemLoader = new DefaultMediaPlayerItemLoader(); 
   itemLoader.addEventListener(MediaPlayerItemLoaderEvent.ERROR, onLoadError); 
   itemLoader.addEventListener(MediaPlayerItemLoaderEvent.COMPLETED, onLoadCompleted); 
   // create the MediaResource instance and set the URL to point to the actual media stream 
   var mediaResource:MediaResource = 
     MediaResource.createFromURL("https://example.com/media/test_media.m3u8", null); 
   // load the media resource 
   itemLoader.load(mediaResource); 
   ```

