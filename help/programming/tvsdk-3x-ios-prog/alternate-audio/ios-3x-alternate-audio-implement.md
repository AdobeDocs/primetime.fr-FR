---
description: Le fichier audio à liaison tardive utilise PTMediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-description: Le fichier audio à liaison tardive utilise PTMediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-title: Accéder à d'autres pistes audio
title: Accéder à d'autres pistes audio
uuid: 2915a74f-5ec3-457e-890d-5c79be39f37a
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Accéder à d&#39;autres pistes audio {#access-alternate-audio-tracks}

Le fichier audio à liaison tardive utilise PTMediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.

1. Attendez que MediaPlayer soit au moins dans l’état `PTMediaPlayerStatusReady`.
1. Écoutez ce événement :

   notification `PTMediaPlayerItemMediaSelectionOptionsAvailable` : La liste initiale des pistes audio est disponible.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. Obtenez les pistes audio disponibles à partir de l&#39;instance `PTMediaPlayerItem`.

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. (Facultatif) Présentez les pistes disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur l&#39;instance `PTMediaPlayerItem`.
