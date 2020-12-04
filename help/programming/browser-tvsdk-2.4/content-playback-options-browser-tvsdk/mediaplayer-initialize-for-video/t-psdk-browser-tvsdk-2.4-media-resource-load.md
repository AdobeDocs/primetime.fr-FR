---
description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire.
seo-description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire.
seo-title: Chargement d’une ressource multimédia dans MediaPlayer
title: Chargement d’une ressource multimédia dans MediaPlayer
uuid: ac31ccfe-161d-41a2-9a6e-38fae11ceab5
translation-type: tm+mt
source-git-commit: 7d61a6cd8cb2c381f85a19d9ccac3d235ffceaf1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Charger une ressource multimédia dans MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire.

1. Définissez l&#39;élément jouable de l&#39;objet `MediaPlayer` avec la nouvelle ressource à lire.

   Remplacez l’élément actuellement lisible de l’objet `MediaPlayer` existant en appelant `replaceCurrentResource` et en transmettant une instance `MediaResource` existante.

1. Attendez que le SDK du navigateur TVSDK distribue `AdobePSDK.MediaPlayerStatusChangeEvent` avec `event.status` qui est égal à l’un des éléments suivants :

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

      Grâce à ces événements, l’objet MediaPlayer informe votre application de la réussite du chargement de la ressource multimédia.

1. Lorsque l&#39;état du lecteur multimédia devient `MediaPlayerStatus.INITIALIZED`, vous pouvez appeler `MediaPlayer.prepareToPlay`.

   L’état INITIALISÉ indique que le chargement du média a réussi. L&#39;appel de `prepareToPlay` début le processus de résolution de publicité et de placement, le cas échéant.
1. Lorsque le navigateur TVSDK distribue le événement `MediaPlayerStatus.PREPARED`, le flux média est chargé avec succès (MediaPlayerItem est créé) et est préparé pour la lecture.

En cas d&#39;échec, `MediaPlayer` passe à `MediaPlayerStatus.ERROR`.

Il informe également votre application en distribuant le événement `MediaPlayerStatus.ERROR`.

><!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->


L’exemple de code simplifié suivant illustre le processus de chargement d’une ressource multimédia :

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                        onStatusChange); 
 
onStatusChange = function (event) { 
    var msg = ""; 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            msg = "Player Status: INITIALIZED"; 
            console.log(msg); 
            player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PREPARED: 
        // The resource is successfully loaded and available 
        // and the MediaPlayer is ready to start the playback. 
        // Once the resource is loaded, the MediaPlayer can 
        // provide a reference to the current "playable item" 
           MediaPlayerItem playerItem = player.currentItem; 
           if (playerItem != null) {  
              // here we can look at the properties of the  
              // loadedstream 
           } 
           break; 
    } 
}
```
