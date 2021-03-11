---
description: Par défaut, lors des débuts de lecture, les débuts de médias VOD à 0 et les débuts de médias en direct au point de production client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
title: Entrer un flux à un moment donné
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
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

