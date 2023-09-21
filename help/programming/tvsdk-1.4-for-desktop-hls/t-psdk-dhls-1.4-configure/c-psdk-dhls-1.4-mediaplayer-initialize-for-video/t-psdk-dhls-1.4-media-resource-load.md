---
description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. Il s’agit d’une méthode de chargement d’une ressource multimédia.
title: Chargement d’une ressource multimédia dans MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Chargement d’une ressource multimédia dans MediaPlayer{#load-a-media-resource-in-the-mediaplayer}

Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. Il s’agit d’une méthode de chargement d’une ressource multimédia.

1. Définissez vos `MediaPlayer` élément lisible de l’objet avec la nouvelle ressource à lire.

   Remplacez l’élément MediaPlayer actuellement lisible existant en appelant `MediaPlayer.replaceCurrentResource` et transmettre un `MediaResource` instance.

1. Recherchez au moins les modifications suivantes :

   * INITIALIZED
   * PRÉPARÉ
   * ERROR

     Au cours de ces événements, `MediaPlayer` peut avertir votre application lorsque la ressource multimédia est chargée avec succès.

1. Lorsque l’état du lecteur multimédia passe à INITIALIZED, vous pouvez appeler `MediaPlayer.prepareToPlay`

   L’état INITIALIZED (INITIALISÉ) indique que le fichier multimédia a bien été chargé. Appel `prepareToPlay` lance le processus de résolution publicitaire et d’emplacement, le cas échéant.

1. Lorsque l’état du lecteur multimédia passe à PREPARED (PRÉPARÉ), le flux multimédia a été chargé avec succès et est préparé pour la lecture.

   Lorsque le flux multimédia est chargé, une `MediaPlayerItem` est créée.

En cas d’échec, le MediaPlayer passe à l’état ERROR. Il informe également votre application en distribuant la variable `STATUS_CHANGED` à votre `MediaPlayerStatusChangeEvent` rappel.

Il transmet plusieurs paramètres :
* A `type` paramètre de type chaîne avec la valeur `ERROR`.

* A `MediaError` que vous pouvez utiliser pour obtenir une notification contenant des informations de diagnostic sur l’événement d’erreur.


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
