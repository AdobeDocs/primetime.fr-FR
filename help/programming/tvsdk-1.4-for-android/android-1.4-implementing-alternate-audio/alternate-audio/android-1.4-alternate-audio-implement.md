---
description: La liaison audio tardive utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-description: La liaison audio tardive utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-title: Accès à d’autres pistes audio
title: Accès à d’autres pistes audio
uuid: c7060022-29ec-43c1-811b-41cca5f5356c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Accès à d’autres pistes audio{#access-alternate-audio-tracks}

La liaison audio tardive utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.

1. Attendez que MediaPlayer soit au moins à l’état PRÉPARÉ.
1. Écoute cette  :

   `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: Le  initial des pistes audio est disponible.

1. Obtenez les pistes audio disponibles à partir de l’ `MediaPlayerItem` instance.

   `mediaPlayerItem.getAudioTracks()` 1. (Facultatif) Présentez les pistes disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur l’ `MediaPlayerItem` instance.

   `mediaPlayerItem.selectAudioTrack(audioTrack)`