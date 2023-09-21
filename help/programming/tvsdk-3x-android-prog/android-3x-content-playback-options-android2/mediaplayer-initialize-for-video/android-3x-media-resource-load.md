---
description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. Il s’agit d’une méthode de chargement d’une ressource multimédia.
title: Chargement d’une ressource multimédia dans le lecteur multimédia
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Chargement d’une ressource multimédia dans le lecteur multimédia {#load-a-media-resource-in-the-media-player}

Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire. Il s’agit d’une méthode de chargement d’une ressource multimédia.

1. Définissez le lecteur multimédia pour lire la nouvelle ressource.

   Remplacez l’élément pouvant être lu en appelant `MediaPlayer.replaceCurrentResource()` et transmettre un `MediaResource` instance.

   Cela permet de lancer le processus de chargement des ressources.

1. Enregistrez le `MediaPlayerEvent.STATUS_CHANGED` avec l’événement `MediaPlayer` instance. Dans le rappel, recherchez au moins les valeurs d’état suivantes :

   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.ERROR`

   Au cours de ces événements, `MediaPlayer` informe votre application lorsqu’elle a correctement chargé la ressource multimédia.
1. Lorsque l’état du lecteur multimédia passe à `INITIALIZED`, vous pouvez appeler `MediaPlayer.prepareToPlay()`.

   Ce statut indique que le fichier multimédia a bien été chargé. La nouvelle `MediaPlayerItem` est prêt pour la lecture. Appel `prepareToPlay()` lance le processus de résolution publicitaire et d’emplacement, le cas échéant.

Si un échec se produit, le lecteur multimédia passe à la fonction `ERROR` statut.

L’exemple de code simplifié suivant illustre le processus de chargement d’une ressource multimédia :

```java>
// mediaResource is a properly configured MediaResource instance 
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
