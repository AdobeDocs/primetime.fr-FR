---
description: Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et qui peut contenir plusieurs flux audio alternatifs.
seo-description: Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et qui peut contenir plusieurs flux audio alternatifs.
seo-title: Accéder à d'autres pistes audio
title: Accéder à d'autres pistes audio
uuid: 09aa00e9-0cbf-4f5b-9652-ce514f6e2f38
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Accéder à d&#39;autres pistes audio{#access-alternate-audio-tracks}

Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et qui peut contenir plusieurs flux audio alternatifs.

1. Attendez qu&#39;ils `MediaPlayer` soient au moins en `MediaPlayerStatus.PREPARED` état.
1. Prêtez attention au `MediaPlayerEvent.STATUS_CHANGED` événement avec le statut `MediaPlayerStatus.PREPARED`.

   Cette étape signifie que la liste initiale des pistes audio est disponible.

1. Récupère les pistes audio disponibles à partir de l&#39; `MediaPlayerItem` instance.

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. (Facultatif) Présentez les pistes disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur l’ `MediaPlayerItem` instance.

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```
