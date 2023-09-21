---
description: Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire.
title: Chargement d’une ressource multimédia dans MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Chargement d’une ressource multimédia dans MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Chargez une ressource en instanciant directement une ressource MediaResource et en chargeant le contenu vidéo à lire.

1. Définissez vos `MediaPlayer` élément lisible de l’objet avec la nouvelle ressource à lire.

   Remplacez votre `MediaPlayer` élément pouvant être lu actuellement en appelant `replaceCurrentResource` et transmettre un `MediaResource` instance.

1. Attendez que le SDK du navigateur soit distribué. `AdobePSDK.MediaPlayerStatusChangeEvent` avec `event.status` qui est égal à l’un des éléments suivants :

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

     Grâce à ces événements, l’objet MediaPlayer indique à votre application si la ressource multimédia a bien été chargée.

1. Lorsque l’état du lecteur multimédia passe à `MediaPlayerStatus.INITIALIZED`, vous pouvez appeler `MediaPlayer.prepareToPlay`.

   L’état INITIALIZED (INITIALISÉ) indique que le fichier multimédia a bien été chargé. Appel `prepareToPlay` lance le processus de résolution publicitaire et d’emplacement, le cas échéant.
1. Lorsque le navigateur TVSDK distribue la variable `MediaPlayerStatus.PREPARED` événement que le flux multimédia a bien chargé (un élément MediaPlayerItem est créé) et est préparé pour la lecture.

Si un échec se produit, la variable `MediaPlayer` passe à la fonction `MediaPlayerStatus.ERROR`.

Il informe également votre application en distribuant la variable `MediaPlayerStatus.ERROR` .

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
