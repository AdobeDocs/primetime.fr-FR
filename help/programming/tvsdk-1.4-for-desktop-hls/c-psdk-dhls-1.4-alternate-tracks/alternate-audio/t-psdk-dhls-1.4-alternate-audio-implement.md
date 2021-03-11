---
description: Les fichiers audio à liaison tardive utilisent MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.
title: Accéder à d'autres pistes audio
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# Accéder à d&#39;autres pistes audio{#access-alternate-audio-tracks}

Les fichiers audio à liaison tardive utilisent MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs flux audio alternatifs.

1. Attendez que `MediaPlayer` soit au moins dans l’état PRÉPARÉ.
1. Prêtez attention aux événements suivants :

   * `MediaPlayerItemEvent.ITEM_CREATED`: La liste initiale des pistes audio est disponible.
   * `MediaPlayerItemEvent.AUDIO_UPDATED`: Suivi audio modifié pendant la lecture

1. Obtenez les pistes audio disponibles à partir de l&#39;instance `MediaPlayerItem`.
1. (Facultatif) Présentez les pistes disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur l&#39;instance `MediaPlayerItem`.
