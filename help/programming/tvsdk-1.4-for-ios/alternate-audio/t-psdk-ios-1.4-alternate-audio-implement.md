---
description: Le fichier audio à liaison tardive utilise PTMediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-description: Le fichier audio à liaison tardive utilise PTMediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-title: Accéder à d'autres pistes audio
title: Accéder à d'autres pistes audio
uuid: 77e39633-bf17-4a06-a2a1-93fdaadedd17
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Accéder à d&#39;autres pistes audio{#access-alternate-audio-tracks}

Le fichier audio à liaison tardive utilise PTMediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.

1. Attendez que MediaPlayer soit au moins dans l’ `PTMediaPlayerStatusReady` état.
1. Écoutez ce événement :

   notification `PTMediaPlayerItemMediaSelectionOptionsAvailable`: La liste initiale des pistes audio est disponible.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. Récupère les pistes audio disponibles à partir de l&#39; `PTMediaPlayerItem` instance.

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. (Facultatif) Présentez les pistes disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur l’ `PTMediaPlayerItem` instance.
