---
description: MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
seo-description: MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
seo-title: Chargement d'une ressource multimédia à l'aide de MediaPlayerItemLoader
title: Chargement d'une ressource multimédia à l'aide de MediaPlayerItemLoader
uuid: a7ec8f58-7357-4757-a402-e879dd6caec8
translation-type: tm+mt
source-git-commit: ''

---


# Chargement d&#39;une ressource multimédia à l&#39;aide de MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader}

MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.

Par le biais de la `MediaPlayerItemLoader` classe, vous pouvez échanger une ressource média pour la ressource correspondante `MediaPlayerItem` sans attacher une vue à une `MediaPlayer` instance, ce qui entraînerait l&#39;allocation des ressources matérielles de décodage vidéo. Le processus d’obtention de l’ `MediaPlayerItem` instance est asynchrone.

1. Mettez en oeuvre des écouteurs de événement pour ces `MediaPlayerItemLoader` événements :

   * `MediaPlayerItemLoaderEvent.ERROR` événement

      TVSDK l’utilise pour informer votre application qu’une erreur s’est produite. TVSDK fournit une propriété d’erreur qui contient des informations de diagnostic.

1. Enregistrez cette instance sur le `MediaPlayerItemLoader`.
1. Appel `DefaultMediaPlayerItemLoader.load`, transmission d’une instance d’un `MediaResource` objet.

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

