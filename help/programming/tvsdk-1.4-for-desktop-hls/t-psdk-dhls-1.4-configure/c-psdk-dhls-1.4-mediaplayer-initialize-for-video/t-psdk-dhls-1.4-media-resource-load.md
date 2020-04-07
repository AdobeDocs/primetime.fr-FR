---
description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. C'est une façon de charger une ressource multimédia.
seo-description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. C'est une façon de charger une ressource multimédia.
seo-title: Chargement d’une ressource multimédia dans MediaPlayer
title: Chargement d’une ressource multimédia dans MediaPlayer
uuid: 8af3e8d1-359d-483c-b394-b95054f7265a
translation-type: tm+mt
source-git-commit: 84924d84bfa436a8807c2e8d74d1dc268d457051

---


# Chargement d’une ressource multimédia dans MediaPlayer{#load-a-media-resource-in-the-mediaplayer}

Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. C&#39;est une façon de charger une ressource multimédia.

1. Définissez l’élément jouable de votre `MediaPlayer` objet avec la nouvelle ressource à lire.

   Remplacez l’élément MediaPlayer actuel que vous utilisez en appelant `MediaPlayer.replaceCurrentResource` et en transmettant une `MediaResource` instance existante.

1. Recherchez au moins les modifications suivantes :

   * INITIALISÉ
   * PRÉPARÉ
   * ERREUR

      Grâce à ces , l’ `MediaPlayer` objet peut avertir votre application lorsque la ressource multimédia est chargée avec succès.

1. Lorsque l’état du lecteur multimédia devient INITIALISÉ, vous pouvez appeler `MediaPlayer.prepareToPlay`

   L’état INITIALIZED indique que le chargement du média a réussi. Appeler le `prepareToPlay` le processus de résolution de publicité et de placement, le cas échéant.

1. Lorsque l’état du lecteur multimédia devient PRÉPARÉ, le flux multimédia est chargé et préparé pour la lecture.

   Lorsque le flux média est chargé, un `MediaPlayerItem` est créé.

En cas d’échec, MediaPlayer passe à l’état ERROR. Il avertit également votre application en distribuant le  `STATUS_CHANGED` à votre `MediaPlayerStatusChangeEvent` rappel.

Il transmet plusieurs paramètres :
* Un `type` paramètre de type chaîne avec la valeur `ERROR`.

* Un `MediaError` paramètre que vous pouvez utiliser pour obtenir une notification contenant des informations de diagnostic sur le  d’erreur.


<!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->

L’exemple de code simplifié suivant illustre le processus de chargement d’une ressource multimédia :

```
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register an event listener with the MediaPlayer instance 
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
private function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
   switch(event.status) { 
      case MediaPlayerStatus.INITIALIZED: 
          // at this point, the resource is successfully loaded 
          // the media player will provide a reference to the current 
          // "playable item" ( is guarantee to be valid and not-null). 
          var playerItem: MediaPlayerItem = mediaPlayer.currentItem; 
          // we can take a look at the media item characteristics like 
          // alternate audio tracks, profile information, if is a live stream 
          // if is drm protected 
          mediaPlayer.prepareToPlay(); 
          break; 
    case MediaPlayerStatus.PREPARED: 
         // at this point, the resource is successfully processed all  
         // advertisement placements have been executed and the the  
         // MediaPlayer is ready to start the playback 
        if (autoPlay) { 
            mediaPlayer.play(); 
        } 
        break; 
    case MediaPlayerStatus.ERROR: 
        // something bad happened - the resource cannot be loaded 
        // details about the problem are provided via the event.error property 
        break; 
        // implementation of the other methods in the PlaybackEventListener interface 
        ... 
    } 
}
```
