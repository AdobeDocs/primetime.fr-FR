---
description: Un objet MediaPlayer encapsule le comportement et les fonctionnalités d’un lecteur multimédia.
seo-description: Un objet MediaPlayer encapsule le comportement et les fonctionnalités d’un lecteur multimédia.
seo-title: Configuration de MediaPlayer
title: Configuration de MediaPlayer
uuid: 2279e388-6fbc-49a2-8560-218d3d31e1d6
translation-type: tm+mt
source-git-commit: af9b865bc1627a97bf8957b5460ff9b46052a7dc

---


# Configuration de MediaPlayer{#set-up-the-mediaplayer}

Un objet MediaPlayer encapsule le comportement et les fonctionnalités d’un lecteur multimédia.

1. Instanciez une `MediaPlayer` application à l’aide des éléments suivants :

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Créez une `MediaPlayerView` instance :

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   où `container` est l’élément de cible `div` qui contient votre `HTMLMediaElement`élément.

   Par exemple, sur une page HTML :

   ```
   <div id="videoDiv"> 
   <codeph>
     <div id="video-controls"> 
          ... custom video controls 
     </div> 
   </codeph> 
   </div>
   ```

   Appel :

   ```js
   var view = new  
   <codeph>
   AdobePSDK.MediaPlayerView 
   </codeph>( 
         document.getElementById("videoDiv"));  
   ```

1. Joignez votre `MediaPlayerView` instance à votre `MediaPlayer` instance :

   ```js
   player.view = view;
   ```

1. Joignez l’élément de contrôle personnalisé `div` à votre instance MediaPlayer.

   Par exemple, en HTML :

   ```
   <div id="videoDiv"> 
      <div id="video-controls"> 
         ..... custom video controls 
      </div> 
   </div>
   ```

   Appel :

   ```js
   if (typeof player.getView() !== 'undefined') { 
       var view = player.view; 
       view.attachVideoControls(document.getElementById("video-controls")); 
   }
   ```

L’ `MediaPlayer` instance est désormais disponible et correctement configurée pour afficher le contenu vidéo sur l’écran du périphérique.
