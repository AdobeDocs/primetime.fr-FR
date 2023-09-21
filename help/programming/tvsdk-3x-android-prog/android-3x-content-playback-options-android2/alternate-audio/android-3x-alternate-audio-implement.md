---
description: L’audio secondaire utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs diffusions audio de remplacement.
title: Accéder à d’autres pistes audio
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Accéder à d’autres pistes audio{#access-alternate-audio-tracks}

L’audio secondaire utilise MediaPlayer pour lire une vidéo spécifiée dans une liste de lecture HLS M3U8 et pouvant contenir plusieurs diffusions audio de remplacement.

1. Attendez que la variable `MediaPlayer` pour être dans au moins la variable `MediaPlayerStatus.PREPARED` statut.
1. Écoute de la `MediaPlayerEvent.STATUS_CHANGED` Événement avec état `MediaPlayerStatus.PREPARED`.

   Cette étape signifie que la liste initiale des pistes audio est disponible.

1. Obtenez les pistes audio disponibles à partir de la fonction `MediaPlayerItem` instance.

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. (Facultatif) Présente les suivis disponibles à l’utilisateur.
1. Définissez la piste audio sélectionnée sur la `MediaPlayerItem` instance.

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```
