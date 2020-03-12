---
description: Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-description: Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-title: Accès à d’autres pistes audio
title: Accès à d’autres pistes audio
uuid: 09aa00e9-0cbf-4f5b-9652-ce514f6e2f38
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Accès à d’autres pistes audio{#access-alternate-audio-tracks}

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
