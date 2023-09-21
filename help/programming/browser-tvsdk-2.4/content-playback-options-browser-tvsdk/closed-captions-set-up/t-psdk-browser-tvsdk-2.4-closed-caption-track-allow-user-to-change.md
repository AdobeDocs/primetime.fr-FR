---
description: Voici un exemple de la manière dont un utilisateur peut sélectionner un suivi de sous-titres non intégrés.
title: Autoriser l’utilisateur à modifier le suivi
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---

# Autoriser l’utilisateur à modifier le suivi{#allow-the-user-to-change-the-track}

Voici un exemple de la manière dont un utilisateur peut sélectionner un suivi de sous-titres non intégrés.

1. Pour afficher les pistes de sous-titres disponibles, utilisez la méthode `MediaPlayerItem.closedCaptionsTracks` .

   ```js
   var tracks = item.closedCaptionsTracks;
   ```

1. Pour définir quel suivi de sous-titres est en cours, utilisez la méthode `MediaPlayerItem.selectClosedCaptionsTrack` .
1. Une fois l’élément du lecteur multimédia préparé, récupérez-le à partir du lecteur multimédia à l’aide de la fonction ` MediaPlayer.  currentItem ` .

   ```js
   // Select the cc track with index k. 
   var item = mediaPlayer.currentItem;     
   var tracks = item.closedCaptionsTracks; 
   
   if (k >= 0 && k < tracks.length) { 
       item.selectClosedCaptionsTrack(tracks[k]); 
   }
   ```
