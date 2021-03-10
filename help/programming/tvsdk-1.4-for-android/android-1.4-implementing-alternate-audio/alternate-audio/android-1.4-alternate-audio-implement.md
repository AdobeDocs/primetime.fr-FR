---
description: Les fichiers audio à liaison tardive utilisent MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
title: Accéder à d'autres pistes audio
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---


# Accéder à d&#39;autres pistes audio{#access-alternate-audio-tracks}

Les fichiers audio à liaison tardive utilisent MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.

1. Attendez que MediaPlayer soit au moins à l’état PRÉPARÉ.
1. Écoutez ce événement :

   `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: La liste initiale des pistes audio est disponible.

1. Obtenez les pistes audio disponibles à partir de l&#39;instance `MediaPlayerItem`.

   `mediaPlayerItem.getAudioTracks()` 1. (Facultatif) Présentez les pistes disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur l&#39;instance `MediaPlayerItem`.

   `mediaPlayerItem.selectAudioTrack(audioTrack)`