---
description: Une autre façon de résoudre une ressource multimédia consiste à utiliser MediaPlayerItemLoader. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.
title: Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

Une autre façon de résoudre une ressource multimédia consiste à utiliser MediaPlayerItemLoader. Cela s’avère utile lorsque vous souhaitez obtenir des informations sur un flux multimédia particulier sans instancier une instance MediaPlayer.

Par le biais de la `MediaPlayerItemLoader` , vous pouvez échanger une ressource multimédia pour la classe correspondante `MediaPlayerItem` sans associer une vue à une `MediaPlayer` , ce qui entraînerait l’allocation des ressources matérielles de décodage vidéo. Le processus d’obtention de la variable `MediaPlayerItem` est asynchrone.

1. Mettez en oeuvre le `MediaPlayerItemLoader.LoaderListener` interface de rappel.

       Cette interface définit deux méthodes :
   
   * `LoaderListener.onError` fonction de rappel

     TVSDK l’utilise pour informer votre application qu’une erreur s’est produite. TVSDK fournit un code d’erreur sous forme de paramètres et une chaîne de description contenant des informations de diagnostic.

   * `LoaderListener.onError` fonction de rappel

     TVSDK l’utilise pour informer votre application que les informations demandées sont disponibles sous la forme d’une `MediaPlayerItem` instance transmise en tant que paramètre au rappel.

1. Enregistrez cette instance à TVSDK en la transmettant en tant que paramètre au constructeur de la variable `MediaPlayerItemLoader`.
1. Appeler `MediaPlayerItemLoader.load`, en transmettant une instance d’une `MediaResource` .

   L’URL de la variable `MediaResource` doit pointer vers le flux pour lequel vous souhaitez obtenir des informations. Par exemple :

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
