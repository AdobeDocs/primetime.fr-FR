---
description: Par défaut, lors des débuts de lecture, les débuts de médias VOD à 0 et les débuts de médias en direct au point de production client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
seo-description: Par défaut, lors des débuts de lecture, les débuts de médias VOD à 0 et les débuts de médias en direct au point de production client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
seo-title: Entrer un flux à un moment donné
title: Entrer un flux à un moment donné
uuid: 5db73b50-0629-4fb1-8f12-6c88e4cd7109
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 1%

---


# Entrer un flux à un moment précis{#enter-a-stream-at-a-specific-time}

Par défaut, lors des débuts de lecture, les débuts de médias VOD à 0 et les débuts de médias en direct au point de production client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.

1. Transmettez une position à `MediaPlayer.prepareToPlay`.
1. Le navigateur TVSDK utilise cette position comme point de départ de la ressource.

   >[!NOTE]
   >
   >Aucune opération de recherche n&#39;est requise.

1. Si la position n’est pas comprise dans la plage recherchée, les positions par défaut sont utilisées.

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

