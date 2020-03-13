---
description: Par défaut, lors de la  de lecture, le de médias VOD  à 0 et lemédia en direct  au point d’accès client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
seo-description: Par défaut, lors de la  de lecture, le de médias VOD  à 0 et lemédia en direct  au point d’accès client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
seo-title: Entrer un flux à un moment spécifique
title: Entrer un flux à un moment spécifique
uuid: 5db73b50-0629-4fb1-8f12-6c88e4cd7109
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Entrer un flux à un moment spécifique{#enter-a-stream-at-a-specific-time}

Par défaut, lors de la  de lecture, le de médias VOD  à 0 et lemédia en direct  au point d’accès client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.

1. Passe une position à `MediaPlayer.prepareToPlay`.
1. Le navigateur TVSDK utilise cette position comme point de départ de la ressource.

   >[!NOTE]
   >
   >Aucune opération de recherche n’est requise.

1. Si la position ne se trouve pas dans la plage recherchée, les positions par défaut sont utilisées.

   Par exemple :

   ```js
   var desiredPostion = //choose a value; 
   onStatusChange = function (event) { 
       case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
           console.log("Player Status: INITIALIZED"); 
           player.prepareToPlay(desiredPostion); 
           break; 
   } 
   ```

