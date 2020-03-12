---
description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire.
seo-description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire.
seo-title: Chargement d’une ressource multimédia dans MediaPlayer
title: Chargement d’une ressource multimédia dans MediaPlayer
uuid: ac31ccfe-161d-41a2-9a6e-38fae11ceab5
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Chargement d’une ressource multimédia dans MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire.

1. Définissez l’élément jouable de votre `MediaPlayer` objet avec la nouvelle ressource à lire.

   Remplacez l’élément actuellement lisible de votre `MediaPlayer` objet existant en appelant `replaceCurrentResource` et en transmettant une `MediaResource` instance existante.

1. Attendez que le SDK du navigateur `AdobePSDK.MediaPlayerStatusChangeEvent` TVSDK soit distribué avec `event.status` ce qui suit :

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

      Par l’intermédiaire de ces , l’objet MediaPlayer indique à votre application si la ressource multimédia a bien été chargée.

1. Lorsque l’état du lecteur multimédia devient `MediaPlayerStatus.INITIALIZED`, vous pouvez appeler `MediaPlayer.prepareToPlay`.

   L’état INITIALIZED indique que le chargement du média a réussi. Appeler le `prepareToPlay` le processus de résolution de publicité et de placement, le cas échéant.
1. Lorsque le navigateur TVSDK distribue le `MediaPlayerStatus.PREPARED` chargé avec succès par le flux média (un MediaPlayerItem est créé), il est préparé pour la lecture.

En cas d’échec, le `MediaPlayer` commutateur passe au `MediaPlayerStatus.ERROR`.

Il avertit également votre application en distribuant le `MediaPlayerStatus.ERROR` .

><!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->


L’exemple de code simplifié suivant illustre le processus de chargement d’une ressource multimédia :

>```js>
>player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
>                                               onStatusChange); 
> 
>
onStatusChange = function (event) { 
>       var msg = ""; 
>       switch (event.status) { 
>               case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
>                       msg = "Player Status: INITIALIZED"; 
>                       console.log(msg); 
>                       player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
>                       break; 
> 
>        
       case AdobePSDK.MediaPlayerStatus.PREPARED: 
>               // The resource is successfully loaded and available 
>               // and the MediaPlayer is ready to start the playback. 
>               // Once the resource is loaded, the MediaPlayer can 
>               // provide a reference to the current "playable item" 
>                     MediaPlayerItem playerItem = player.currentItem; 
>                     if (playerItem != null) {  
>                           // here we can look at the properties of the  
>                           // loadedstream 
>                     } 
>                     break; 
>       } 
>}
>```>


