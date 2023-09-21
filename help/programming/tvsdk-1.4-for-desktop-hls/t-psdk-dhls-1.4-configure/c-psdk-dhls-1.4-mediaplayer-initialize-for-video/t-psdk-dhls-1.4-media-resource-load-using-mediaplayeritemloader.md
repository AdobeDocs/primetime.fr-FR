---
description: Une autre façon de résoudre une ressource multimédia consiste à utiliser MediaPlayerItemLoader. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
title: Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader}

Une autre façon de résoudre une ressource multimédia consiste à utiliser MediaPlayerItemLoader. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.

Par le biais de la `MediaPlayerItemLoader` , vous pouvez échanger une ressource multimédia pour la classe correspondante `MediaPlayerItem` sans associer une vue à une `MediaPlayer` , ce qui entraînerait l’allocation des ressources matérielles de décodage vidéo. Le processus d’obtention de la variable `MediaPlayerItem` est asynchrone.

1. Mise en oeuvre d’écouteurs d’événement pour ces `MediaPlayerItemLoader` events :

   * `MediaPlayerItemLoaderEvent.ERROR` event

     TVSDK l’utilise pour informer votre application qu’une erreur s’est produite. TVSDK fournit une propriété d’erreur qui contient des informations de diagnostic.

1. Enregistrez cette instance dans la `MediaPlayerItemLoader`.
1. Appeler `DefaultMediaPlayerItemLoader.load`, en transmettant une instance d’une `MediaResource` .

   L’URL de la variable `MediaResource` doit pointer vers le flux pour lequel vous souhaitez obtenir des informations. Par exemple :

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
