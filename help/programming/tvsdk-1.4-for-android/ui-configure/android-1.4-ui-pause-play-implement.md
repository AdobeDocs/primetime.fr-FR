---
description: Vous pouvez ajouter un comportement TVSDK pour mettre en pause et lire des boutons.
title: Lecture et mise en pause d’une vidéo
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Lecture et mise en pause d’une vidéo {#play-and-pause-a-video}

Vous pouvez ajouter un comportement TVSDK pour mettre en pause et lire des boutons.

1. Créez un bouton Pause/Lecture qui effectue les opérations suivantes.
   1. Attendez que votre lecteur soit au moins à l’état PRÉPARÉ.
   1. Pour début la lecture, appelez la méthode de lecture TVSDK :

      ```java
      void play() throws IllegalStateException;
      ```

   1. Pour mettre la lecture en pause, appelez la méthode de mise en pause TVSDK :

      ```java
      void pause() throws IllegalStateException;
      ```

1. Utilisez le rappel `MediaPlayer.PlaybackEventListener.onStateChanged` pour rechercher les erreurs ou pour effectuer d&#39;autres actions appropriées.

   TVSDK appelle ce rappel lorsque la méthode pause ou play est appelée. TVSDK transmet des informations sur la modification de l’état dans le rappel, y compris le nouvel état, tel que PAUSED ou PLAYING.

