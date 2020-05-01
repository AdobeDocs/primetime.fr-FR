---
description: Les fichiers audio à liaison tardive utilisent MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-description: Les fichiers audio à liaison tardive utilisent MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-title: Accéder à d'autres pistes audio
title: Accéder à d'autres pistes audio
uuid: c7060022-29ec-43c1-811b-41cca5f5356c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Accéder à d&#39;autres pistes audio{#access-alternate-audio-tracks}

Les fichiers audio à liaison tardive utilisent MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.

1. Attendez que MediaPlayer soit au moins à l’état PRÉPARÉ.
1. Écoutez ce événement :

   `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: La liste initiale des pistes audio est disponible.

1. Récupère les pistes audio disponibles à partir de l&#39; `MediaPlayerItem` instance.

   `mediaPlayerItem.getAudioTracks()` 1. (Facultatif) Présentez les pistes disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur l’ `MediaPlayerItem` instance.

   `mediaPlayerItem.selectAudioTrack(audioTrack)`