---
description: Voici un exemple de la façon dont un utilisateur peut sélectionner un suivi de sous-titrage fermé.
title: Autoriser l’utilisateur à modifier le suivi
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---


# Autoriser l’utilisateur à modifier le suivi {#allow-the-user-to-change-the-track}

Voici un exemple de la façon dont un utilisateur peut sélectionner un suivi de sous-titrage fermé.

1. Pour afficher les pistes de sous-titrage disponibles, utilisez la propriété `MediaPlayerItem.closedCaptionsTracks`.

   ```js
   var tracks = item.closedCaptionsTracks;
   ```

1. Pour définir quel suivi de sous-titrage est en cours, utilisez la méthode `MediaPlayerItem.selectClosedCaptionsTrack`.
1. Une fois l&#39;élément du lecteur multimédia préparé, récupérez-le du lecteur multimédia à l&#39;aide de la méthode ` MediaPlayer.  currentItem `.

   ```js
   // Select the cc track with index k. 
   var item = mediaPlayer.currentItem;     
   var tracks = item.closedCaptionsTracks; 
   
   if (k >= 0 && k < tracks.length) { 
       item.selectClosedCaptionsTrack(tracks[k]); 
   }
   ```

