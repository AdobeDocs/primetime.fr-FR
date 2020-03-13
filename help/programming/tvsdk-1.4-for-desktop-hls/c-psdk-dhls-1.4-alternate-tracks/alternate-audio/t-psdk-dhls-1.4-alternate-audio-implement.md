---
description: La liaison audio tardive utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-description: La liaison audio tardive utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
seo-title: Accès à d’autres pistes audio
title: Accès à d’autres pistes audio
uuid: 136b4f1b-e56f-4a8a-a961-05193434558c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Accès à d’autres pistes audio{#access-alternate-audio-tracks}

La liaison audio tardive utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.

1. Attendez que le `MediaPlayer` soit dans au moins l’état PRÉPARÉ.
1. Ecoutez ces  :

   * `MediaPlayerItemEvent.ITEM_CREATED`: Le  initial des pistes audio est disponible.
   * `MediaPlayerItemEvent.AUDIO_UPDATED`: Suivi audio modifié pendant la lecture

1. Obtenez les pistes audio disponibles à partir de l’ `MediaPlayerItem` instance.
1. (Facultatif) Présentez les pistes disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur l’ `MediaPlayerItem` instance.
