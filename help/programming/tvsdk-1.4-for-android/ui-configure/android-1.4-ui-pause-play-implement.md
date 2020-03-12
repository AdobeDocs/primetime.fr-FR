---
description: Vous pouvez ajouter un comportement TVSDK pour mettre en pause et lire des boutons.
seo-description: Vous pouvez ajouter un comportement TVSDK pour mettre en pause et lire des boutons.
seo-title: Lecture et mise en pause d’une vidéo
title: Lecture et mise en pause d’une vidéo
uuid: 24b26364-5cb8-4a95-9574-cc52ddfa876b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Lecture et mise en pause d’une vidéo{#play-and-pause-a-video}

Vous pouvez ajouter un comportement TVSDK pour mettre en pause et lire des boutons.

1. Créez un bouton Pause/Lecture qui effectue les opérations suivantes.
   1. Attendez que votre joueur soit dans l&#39;état PRÉPARÉ.
   1. Pour  lecture, appelez la méthode de lecture TVSDK :

      ```java
      void play() throws IllegalStateException;
      ```

   1. Pour mettre la lecture en pause, appelez la méthode de mise en pause TVSDK :

      ```java
      void pause() throws IllegalStateException;
      ```

1. Utilisez le `MediaPlayer.PlaybackEventListener.onStateChanged` rappel pour rechercher les erreurs ou pour effectuer d’autres actions appropriées.

   TVSDK appelle ce rappel lorsque la méthode pause ou play est appelée. TVSDK transmet des informations sur le changement d’état dans le rappel, y compris le nouvel état, tel que PAUSED ou PLAYING.

