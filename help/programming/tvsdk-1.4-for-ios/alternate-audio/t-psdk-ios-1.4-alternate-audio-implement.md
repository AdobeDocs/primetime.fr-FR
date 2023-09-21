---
description: Le contenu audio à liaison tardive utilise PTMediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs autres diffusions audio.
title: Accéder à d’autres pistes audio
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# Accéder à d’autres pistes audio{#access-alternate-audio-tracks}

Le contenu audio à liaison tardive utilise PTMediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs autres diffusions audio.

1. Attendez que MediaPlayer soit dans au moins la variable `PTMediaPlayerStatusReady` statut.
1. Prêtez attention à cet événement :

   notification `PTMediaPlayerItemMediaSelectionOptionsAvailable`: la liste initiale des pistes audio est disponible.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. Obtenez les pistes audio disponibles à partir de la fonction `PTMediaPlayerItem` instance.

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. (Facultatif) Présente les suivis disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur la `PTMediaPlayerItem` instance.
