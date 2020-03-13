---
description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. C'est une façon de charger une ressource multimédia.
seo-description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. C'est une façon de charger une ressource multimédia.
seo-title: Chargement d’une ressource multimédia dans le lecteur de médias
title: Chargement d’une ressource multimédia dans le lecteur de médias
uuid: 0334fa69-1d92-44d8-8891-2bc90a1ea498
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Chargement d’une ressource multimédia dans le lecteur de médias {#load-a-media-resource-in-the-media-player}

Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. C&#39;est une façon de charger une ressource multimédia.

1. Définissez le lecteur de médias pour lire la nouvelle ressource.

   Remplacez l’élément actuellement lisible en appelant `MediaPlayer.replaceCurrentResource()` et en transmettant une `MediaResource` instance existante.

   Ce  le processus de chargement des ressources.

1. Enregistrez le `MediaPlayerEvent.STATUS_CHANGED` avec l’ `MediaPlayer` instance. Dans le rappel, recherchez au moins les valeurs d’état suivantes :

   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.ERROR`
   Par l’intermédiaire de ces , l’ `MediaPlayer` objet avertit votre application lorsqu’elle a correctement chargé la ressource multimédia.
1. Lorsque l’état du lecteur multimédia devient `INITIALIZED`, vous pouvez appeler `MediaPlayer.prepareToPlay()`.

   Cet état indique que le chargement du média a réussi. Le nouveau `MediaPlayerItem` est prêt pour la lecture. Appeler le `prepareToPlay()` le processus de résolution de publicité et de placement, le cas échéant.

En cas d’échec, le lecteur de médias passe à l’ `ERROR` état.

L’exemple de code simplifié suivant illustre le processus de chargement d’une ressource multimédia :
>```java>
>// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register a PlaybackEventListener implementation with the MediaPlayer instance 
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
 new StatusChangeEventListener() { 
   @Override 
   public void onStatusChanged(MediaPlayerStatus status) { 
       if(event.getStatus() == MediaPlayerStatus.PREPARED) { 
           // The resource is successfully loaded and available. The  
           // MediaPlayer is ready to start the playback and can 
           // provide a reference to the current playable item 
           MediaPlayerItem playerItem = mediaPlayer.getCurrentItem(); 
           if (playerItem != null) { 
               // We can look at the properties of the loaded stream 
           } 
       } 
       else if (event.getStatus() == MediaPlayerStatus.ERROR) { 
           //Something bad happened - the resource cannot be loaded. 
           // The Metadata object in the event provides details. 
       } 
       else if (status == MediaPlayerStatus.INITIALIZED) { 
           mediaPlayer.prepareToPlay(); 
       } 
   } 
} 
```
