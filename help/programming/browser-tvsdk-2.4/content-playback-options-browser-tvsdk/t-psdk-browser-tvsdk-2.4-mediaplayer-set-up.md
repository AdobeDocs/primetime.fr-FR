---
description: Un objet MediaPlayer encapsule le comportement et les fonctionnalités d’un lecteur multimédia.
title: Configuration de MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Configuration de MediaPlayer{#set-up-the-mediaplayer}

Un objet MediaPlayer encapsule le comportement et les fonctionnalités d’un lecteur multimédia.

1. Instanciation d’une `MediaPlayer` à l’aide des éléments suivants :

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Créez un `MediaPlayerView` instance :

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   where `container` est la cible `div` élément qui contient votre `HTMLMediaElement`.

   Par exemple, sur une page de HTML :

   ```
   <div id="videoDiv"> 
   <codeph>
     <div id="video-controls"> 
          ... custom video controls 
     </div> 
   </codeph> 
   </div>
   ```

   Appelez :

   ```js
   var view = new  
   <codeph>
   AdobePSDK.MediaPlayerView 
   </codeph>( 
         document.getElementById("videoDiv"));  
   ```

1. Joindre vos `MediaPlayerView` à votre instance `MediaPlayer` instance :

   ```js
   player.view = view;
   ```

1. Joindre les contrôles personnalisés `div` à votre instance MediaPlayer.

   Par exemple, en HTML :

   ```
   <div id="videoDiv"> 
      <div id="video-controls"> 
         ..... custom video controls 
      </div> 
   </div>
   ```

   Appelez :

   ```js
   if (typeof player.getView() !== 'undefined') { 
       var view = player.view; 
       view.attachVideoControls(document.getElementById("video-controls")); 
   }
   ```

La variable `MediaPlayer` est maintenant disponible et correctement configurée pour afficher le contenu vidéo sur l’écran de l’appareil.
