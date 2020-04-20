---
description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. C'est une façon de charger une ressource multimédia.
seo-description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. C'est une façon de charger une ressource multimédia.
seo-title: Chargement d’une ressource multimédia dans MediaPlayer
title: Chargement d’une ressource multimédia dans MediaPlayer
uuid: 6ee8032f-0728-423f-a1d2-5030aa7db14f
translation-type: tm+mt
source-git-commit: 4ef05be045334a2e723da4c7c6a7ee22fb0f776c

---


# Chargement d’une ressource multimédia dans MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. C&#39;est une façon de charger une ressource multimédia.

1. Définissez l’élément lisible de votre lecteur multimédia avec la nouvelle ressource à lire.

   Remplacez l’élément MediaPlayer actuel que vous utilisez en appelant `MediaPlayer.replaceCurrentItem` et en transmettant une `MediaResource` instance existante.

1. Enregistrez une implémentation de l’ `MediaPlayer.PlaybackEventListener` interface avec l’ `MediaPlayer` instance.

   * `onPrepared`
   * `onStateChanged`, puis recherchez INITIALIZED et ERROR.

1. Lorsque l’état du lecteur multimédia devient INITIALISÉ, vous pouvez appeler `MediaPlayer.prepareToPlay`

   L’état INITIALIZED indique que le chargement du média a réussi. Appeler le `prepareToPlay` le processus de résolution de publicité et de placement, le cas échéant.

1. Lorsque TVSDK appelle le `onPrepared` rappel, le flux média a été chargé avec succès et est préparé pour la lecture.

   Lorsque le flux média est chargé, un `MediaPlayerItem` est créé.

>En cas d’échec, le `MediaPlayer` commutateur passe à l’état ERROR. Il informe également votre application en appelant votre `PlaybackEventListener.onStateChanged`rappel.
>
>Il transmet plusieurs paramètres :
>* Un `state` paramètre de type `MediaPlayer.PlayerState` avec la valeur de `MediaPlayer.PlayerState.ERROR`.
   >
   >
* Un `notification` paramètre de type `MediaPlayerNotification` qui contient des informations de diagnostic sur le  d’erreur.


L’exemple de code simplifié suivant illustre le processus de chargement d’une ressource multimédia :

```java
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register a PlaybackEventListener implementation with the MediaPlayer  
instancemediaPlayer.addEventListener( 
  MediaPlayer.Event.PLAYBACK, 
  new MediaPlayer.PlaybackEventListener()) { 
    @Overridepublic void onPrepared() { 
        // at this point, the resource is successfully loaded and available 
        // and the MediaPlayer is ready to start the playback 
        // once the resource is loaded, the MediaPlayer is able to 
        // provide a reference to the current "playable item" 
 
        MediaPlayerItem playerItem = mediaPlayer.CurrentItem(); 
 
        if (playerItem != null) {     
            // here we can take a look at the properties of the     
            // loaded stream 
        } 
    } @Overridepublic void onStateChanged( 
        MediaPlayer.PlayerState state,  
        MediaPlayerNotification notification) { 
        if (state == MediaPlayer.PlayerState.ERROR) { 
            // something bad happened - the resource cannot be loaded    
            // details about the problem are provided via the  
            // MediaPlayerNotification instance 
        }  
        elseif (state == MediaPlayer.PlayerState.INITIALIZED) {     
            mediaPlayer.prepareToPlay(); 
        } 
    } 
    // implementation of the other methods in the PlaybackEventListener interface... 
} 
```
