---
description: Un objet MediaPlayer encapsule le comportement et les fonctionnalités d’un lecteur multimédia.
title: Configuration de MediaPlayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---


# Configuration de MediaPlayer{#set-up-the-mediaplayer}

Un objet MediaPlayer encapsule le comportement et les fonctionnalités d’un lecteur multimédia.

1. Instanciez un `MediaPlayer` à l&#39;aide des éléments suivants :

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Créez une instance `MediaPlayerView` :

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   où `container` est l’élément de cible `div` qui contient votre `HTMLMediaElement`.

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

1. Joignez votre instance `MediaPlayerView` à votre instance `MediaPlayer` :

   ```js
   player.view = view;
   ```

1. Joignez l’élément `div` contrôles personnalisés à votre instance MediaPlayer.

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

L&#39;instance `MediaPlayer` est désormais disponible et correctement configurée pour afficher le contenu vidéo sur l&#39;écran du périphérique.
