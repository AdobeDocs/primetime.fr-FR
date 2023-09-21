---
description: Par défaut, au démarrage de la lecture, le média VOD démarre à 0 et le média en direct à partir du point d’activation du client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
title: Saisie d’un flux à un moment spécifique
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Saisie d’un flux à un moment spécifique{#enter-a-stream-at-a-specific-time}

Par défaut, au démarrage de la lecture, le média VOD démarre à 0 et le média en direct à partir du point d’activation du client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.

1. Transmettre une position à `MediaPlayer.prepareToPlay`.
1. Le TVSDK du navigateur utilise cette position comme point de départ de la ressource.

   >[!NOTE]
   >
   >Aucune opération de recherche n’est requise.

1. Si la position ne se trouve pas dans la plage pouvant faire l’objet d’une recherche, les positions par défaut sont utilisées.

   Par exemple :

   ```js
   var desiredPostion = //choose a value; 
   onStatusChange = function (event) { 
       case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
           console.log("Player Status: INITIALIZED"); 
           player.prepareToPlay(desiredPostion); 
           break; 
   } 
   ```
