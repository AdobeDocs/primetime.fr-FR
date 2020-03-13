---
description: MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
seo-description: MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
seo-title: Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader
title: Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader
uuid: a7ec8f58-7357-4757-a402-e879dd6caec8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader}

MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.

Grâce à la `MediaPlayerItemLoader` classe, vous pouvez échanger une ressource multimédia pour la ressource `MediaPlayerItem` correspondante sans attacher un à une `MediaPlayer` instance, ce qui conduirait à l&#39;allocation des ressources matérielles de décodage vidéo. Le processus d’obtention de l’ `MediaPlayerItem` instance est asynchrone.

1. Mettez en oeuvre des écouteurs  pour ces  de : `MediaPlayerItemLoader`

   * `MediaPlayerItemLoaderEvent.ERROR` 

      TVSDK l’utilise pour informer votre application qu’une erreur s’est produite. TVSDK fournit une propriété d’erreur qui contient des informations de diagnostic.

1. Enregistrez cette instance dans le `MediaPlayerItemLoader`.
1. Appelez `DefaultMediaPlayerItemLoader.load`, en transmettant une instance d’un `MediaResource` objet.

   L’URL de l’ `MediaResource` objet doit pointer vers le flux pour lequel vous souhaitez obtenir des informations. Par exemple :

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

