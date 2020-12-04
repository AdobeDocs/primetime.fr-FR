---
description: MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
seo-description: MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
seo-title: Chargement d'une ressource multimédia à l'aide de MediaPlayerItemLoader
title: Chargement d'une ressource multimédia à l'aide de MediaPlayerItemLoader
uuid: b2311ddc-f059-4775-8553-fc354ec2636b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# Charger une ressource multimédia à l&#39;aide de MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

MediaPlayerItemLoader permet également de résoudre une ressource multimédia. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.

Par l&#39;intermédiaire de la classe `MediaPlayerItemLoader`, vous pouvez échanger une ressource média pour le `MediaPlayerItem` correspondant sans attacher une vue à une instance `MediaPlayer`, ce qui conduirait à l&#39;allocation des ressources matérielles de décodage vidéo. Le processus d&#39;obtention de l&#39;instance `MediaPlayerItem` est asynchrone.

1. Implémentez l&#39;interface de rappel `MediaPlayerItemLoader.LoaderListener`.

       Cette interface définit deux méthodes :
   
   * `LoaderListener.onError` fonction de rappel

      TVSDK l’utilise pour informer votre application qu’une erreur s’est produite. TVSDK fournit un code d’erreur sous forme de paramètres et une chaîne de description contenant des informations de diagnostic.

   * `LoaderListener.onError` fonction de rappel

      TVSDK l’utilise pour informer votre application que les informations demandées sont disponibles sous la forme d’une instance `MediaPlayerItem` transmise en tant que paramètre au rappel.

1. Enregistrez cette instance auprès de TVSDK en la transmettant en tant que paramètre au constructeur de `MediaPlayerItemLoader`.
1. Appelez `MediaPlayerItemLoader.load`, en transmettant une instance d&#39;un objet `MediaResource`.

   L&#39;URL de l&#39;objet `MediaResource` doit pointer vers le flux pour lequel vous souhaitez obtenir des informations. Par exemple :

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

