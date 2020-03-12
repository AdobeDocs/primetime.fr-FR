---
description: MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
seo-description: MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
seo-title: Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader
title: Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader
uuid: b2311ddc-f059-4775-8553-fc354ec2636b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.

Grâce à la `MediaPlayerItemLoader` classe, vous pouvez échanger une ressource multimédia pour la ressource `MediaPlayerItem` correspondante sans attacher un à une `MediaPlayer` instance, ce qui conduirait à l&#39;allocation des ressources matérielles de décodage vidéo. Le processus d’obtention de l’ `MediaPlayerItem` instance est asynchrone.

1. Implémentez l’interface de `MediaPlayerItemLoader.LoaderListener` rappel.

       Cette interface définit deux méthodes :
   
   * `LoaderListener.onError` callback, fonction

      TVSDK l’utilise pour informer votre application qu’une erreur s’est produite. TVSDK fournit un code d’erreur sous forme de paramètres et une chaîne de description contenant des informations de diagnostic.

   * `LoaderListener.onError` callback, fonction

      TVSDK l’utilise pour informer votre application que les informations demandées sont disponibles sous la forme d’une `MediaPlayerItem` instance transmise en tant que paramètre au rappel.

1. Enregistrez cette instance dans TVSDK en la transmettant comme paramètre au constructeur du `MediaPlayerItemLoader`.
1. Appelez `MediaPlayerItemLoader.load`, en transmettant une instance d’un `MediaResource` objet.

   L’URL de l’ `MediaResource` objet doit pointer vers le flux pour lequel vous souhaitez obtenir des informations. Par exemple :

   ```java
   // instantiate the listener interface 
   MediaPlayerItemLoader.LoaderListener _itemLoaderListener = 
     new MediaPlayerItemLoader.LoaderListener() { 
       @Override 
       public void onError(MediaErrorCode mediaErrorCode, String description) { 
           // something went wrong - look at the error code and description 
       } 
       @Override 
           public void onLoadComplete(MediaPlayerItem playerItem) { 
           // information is available - look at the data in the "playerItem" object 
       } 
   } 
   
   // instantiate the MediaPlayerItemLoader object (pass the listener as parameter) 
   MediaPlayerItemLoader itemLoader = new MediaPlayerItemLoader(_itemLoaderListener); 
   
   // create the MediaResource instance and set the URL to point to the actual media stream 
   MediaResource mediaResource =  
     MediaResource.createFromUrl("https://test.com/test_media.m3u8", null); 
   
   // load the media resource 
   itemLoader.load(mediaResource); 
   ```

