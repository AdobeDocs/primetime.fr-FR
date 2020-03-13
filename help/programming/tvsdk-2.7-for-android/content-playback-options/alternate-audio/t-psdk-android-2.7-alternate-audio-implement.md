---
description: Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-description: Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-title: Accès à d’autres pistes audio
title: Accès à d’autres pistes audio
uuid: 9cec3a00-1416-497d-8d16-0ee429c8b575
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Accès à d’autres pistes audio {#access-alternate-audio-tracks}

Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.

1. Attendez que le `MediaPlayer` soit dans au moins le `MediaPlayerStatus.PREPARED` statut.
1. Écoute le `MediaPlayerEvent.STATUS_CHANGED` avec le statut `MediaPlayerStatus.PREPARED`.

   Cette étape signifie que le  initial des pistes audio est disponible.

1. Obtenez les pistes audio disponibles à partir de l’ `MediaPlayerItem` instance.

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. (Facultatif) Présentez les pistes disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur l’ `MediaPlayerItem` instance.

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```

