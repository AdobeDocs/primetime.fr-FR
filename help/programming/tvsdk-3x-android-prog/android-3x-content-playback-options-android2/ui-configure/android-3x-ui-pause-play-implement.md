---
description: Vous pouvez ajouter des boutons Pause et Lecture pour suspendre ou lire la vidéo.
seo-description: Vous pouvez ajouter des boutons Pause et Lecture pour suspendre ou lire la vidéo.
seo-title: Lecture et mise en pause d’une vidéo
title: Lecture et mise en pause d’une vidéo
uuid: 3778a1fb-929c-4579-a14c-561179473dea
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Lecture et mise en pause d’une vidéo {#play-and-pause-a-video}

Vous pouvez ajouter des boutons Pause et Lecture pour suspendre ou lire la vidéo.

1. Pour créer un bouton de pause ou de lecture :
   1. Attendez que le joueur soit au moins dans l&#39;état préparé.
   1. Pour début la lecture, appelez la `play` méthode :

      ```java
      void play() throws MediaPlayerException;
      ```

   1. Pour interrompre la lecture, appelez la `pause()` méthode :

      ```java
      void pause() throws MediaPlayerException;
      ```

1. Utilisez le rappel de événement d’état modifié pour rechercher les erreurs ou pour effectuer d’autres actions appropriées.

   TVSDK appelle ce rappel pour `pause()` ou `play()` et transmet des informations sur le changement d’état, y compris le nouveau statut, tel que suspendu ou en cours de lecture.