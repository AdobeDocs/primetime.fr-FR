---
description: Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et qui peut contenir plusieurs flux audio alternatifs.
seo-description: Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et qui peut contenir plusieurs flux audio alternatifs.
seo-title: Accéder à d'autres pistes audio
title: Accéder à d'autres pistes audio
uuid: 9cec3a00-1416-497d-8d16-0ee429c8b575
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---


# Accéder à d&#39;autres pistes audio {#access-alternate-audio-tracks}

Le son alternatif utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et qui peut contenir plusieurs flux audio alternatifs.

1. Attendez que `MediaPlayer` se trouve au moins dans l&#39;état `MediaPlayerStatus.PREPARED`.
1. Prêtez attention au événement `MediaPlayerEvent.STATUS_CHANGED` avec le statut `MediaPlayerStatus.PREPARED`.

   Cette étape signifie que la liste initiale des pistes audio est disponible.

1. Obtenez les pistes audio disponibles à partir de l&#39;instance `MediaPlayerItem`.

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. (Facultatif) Présentez les pistes disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur l&#39;instance `MediaPlayerItem`.

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```

