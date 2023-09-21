---
description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. Il s’agit d’une méthode de chargement d’une ressource multimédia.
title: Chargement d’une ressource multimédia dans MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Chargement d’une ressource multimédia dans MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. Il s’agit d’une méthode de chargement d’une ressource multimédia.

1. Définissez l’élément lisible de votre lecteur multimédia avec la nouvelle ressource à lire.

   Remplacez l’élément MediaPlayer actuellement lisible existant en appelant `MediaPlayer.replaceCurrentItem` et transmettre un `MediaResource` instance.

1. Enregistrez une implémentation de la fonction `MediaPlayer.PlaybackEventListener` avec l’interface `MediaPlayer` instance.

   * `onPrepared`
   * `onStateChanged`et recherchez INITIALISED et ERROR.

1. Lorsque l’état du lecteur multimédia passe à INITIALIZED, vous pouvez appeler `MediaPlayer.prepareToPlay`

   L’état INITIALIZED (INITIALISÉ) indique que le fichier multimédia a bien été chargé. Appel `prepareToPlay` lance le processus de résolution publicitaire et d’emplacement, le cas échéant.

1. Lorsque TVSDK appelle la variable `onPrepared` , le flux multimédia a été chargé avec succès et est préparé pour la lecture.

   Lorsque le flux multimédia est chargé, une `MediaPlayerItem` est créée.

>Si un échec se produit, la variable `MediaPlayer` passe au statut ERROR. Il informe également votre application en appelant votre `PlaybackEventListener.onStateChanged`rappel.
>
>Il transmet plusieurs paramètres :
>* A `state` paramètre de type `MediaPlayer.PlayerState` avec la valeur de `MediaPlayer.PlayerState.ERROR`.
>
>* A `notification` paramètre de type `MediaPlayerNotification` qui contient des informations de diagnostic sur l’événement d’erreur.

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
