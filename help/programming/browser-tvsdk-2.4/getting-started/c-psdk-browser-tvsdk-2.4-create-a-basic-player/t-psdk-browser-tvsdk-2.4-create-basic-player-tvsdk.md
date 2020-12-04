---
description: Suivez les étapes ci-après pour créer un lecteur de base à l’aide du SDK du navigateur.
seo-description: Suivez les étapes ci-après pour créer un lecteur de base à l’aide du SDK du navigateur.
seo-title: Création d’un lecteur de base à l’aide de TVSDK
title: Création d’un lecteur de base à l’aide de TVSDK
uuid: ec15cf53-197f-4190-a6b2-600a57815390
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Créez un lecteur de base à l’aide de TVSDK{#create-a-basic-player-using-tvsdk}

Suivez les étapes ci-après pour créer un lecteur de base à l’aide du SDK du navigateur.

1. Créez un répertoire dans lequel vous pouvez télécharger les fichiers compressés pour le SDK Browser TVSDK.
1. Téléchargez le navigateur TVSDK à partir de Zendesk, décompressez les fichiers et importez le dossier infrastructures dans le nouveau répertoire.
1. Créez un modèle standard HTML simple pour le code contenant un `div`.
1. Placez ce standard dans un fichier HTML dans le répertoire que vous avez créé à l’étape 1.

   ```
   <!DOCTYPE html> 
   
   <html lang="en"> 
   <head> 
   </head> 
   <body> 
         <div id="videoDiv" width="200" height="200"> 
        <div id="video-controls"></div> 
         </div> 
   </body> 
   </html>
   ```

1. Ajoutez les bibliothèques du navigateur TVSDK dans la section head.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script>
   ```

1. Pour la balise body, ajoutez la section `onLoad`.

   ```
   <body onload="startVideo()">
   ```

1. Début implémentant la fonction `startVideo`.
1. Ajoutez une balise de script et créez la fonction `startVideo` dans la balise .

   Il est censé se trouver dans la section head de la page.

   ```js
   <script> 
    function startVideo(){ 
    } 
   </script>
   ```

1. Créez le `Adobe.MediaPlayer`.

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Créez le `MediaPlayerView`.

   >[!TIP]
   >
   >C&#39;est là que le `div` que vous avez créé précédemment est utilisé.

   ```js
   var view = new AdobePSDK.MediaPlayerView( 
   document.getElementById("videoDiv")); 
   player.view = view;
   ```

1. Ajoutez l’écouteur de événement du lecteur.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. Mettez en oeuvre le gestionnaire de événements et placez-le avant l’écouteur de événement ajouté.

   ```js
   var onStatusChange = function (event) { 
    console.log(event.status); 
   
    switch (event.status) { 
     case AdobePSDK.MediaPlayerStatus.IDLE: 
      console.log("Player Status: IDLE"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.INITIALIZING: 
      console.log("Player Status: INITIALIZING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
      console.log("Player Status: INITIALIZED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PREPARING: 
      console.log("Player Status: PREPARING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PREPARED: 
      console.log("Player Status: PREPARED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PLAYING: 
      console.log("Player Status: PLAYING"); 
      //update UI play/pause to show pause icon 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PAUSED: 
      console.log("Player Status: PAUSED"); 
      //update UI play/pause to show play icon & 
      //display pause icon over video 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.SEEKING: 
      console.log("Player Status: SEEKING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.COMPLETE: 
      console.log("Player Status: COMPLETE"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.RELEASED: 
      console.log("Player Status: RELEASED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.RELEASED: 
      console.log("Player Status: ERROR"); 
      break; 
    } 
   }; 
   ```

1. Créez le `MediaResource`, qui transmet le lien M3U8 (ou mpd).

   ```js
   var resourceUrl = "https://example.com/a/yourUrl.m3u8"; 
   var resourceType = AdobePSDK.MediaResourceType.HLS; 
   var mediaResource = new AdobePSDK.MediaResource(resourceUrl, resourceType, null, false);
   ```

1. Créez une configuration vide et remplacez la ressource.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   
   player.replaceCurrentResource(mediaResource, config);
   ```

1. Lorsque le lecteur est à l’état INITIALISÉ, appelez `prepareToPlay`.

   ```js
   case INITIALIZED: 
    player.prepareToPlay(); // <- add this line 
    break;
   ```

1. Une fois que le lecteur est à l’état PRÉPARÉ, appelez `play`.

   ```js
   case PREPARED: 
    player.play(); 
    break;
   ```

