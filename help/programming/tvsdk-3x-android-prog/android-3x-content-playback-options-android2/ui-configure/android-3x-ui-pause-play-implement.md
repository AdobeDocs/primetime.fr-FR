---
description: Vous pouvez ajouter des boutons Pause et Lecture pour suspendre ou lire la vidéo.
title: Lecture et mise en pause d’une vidéo
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---


# Lecture et mise en pause d’une vidéo {#play-and-pause-a-video}

Vous pouvez ajouter des boutons Pause et Lecture pour suspendre ou lire la vidéo.

1. Pour créer un bouton de pause ou de lecture :
   1. Attendez que le joueur soit au moins dans l&#39;état préparé.
   1. Pour début la lecture, appelez la méthode `play` :

      ```java
      void play() throws MediaPlayerException;
      ```

   1. Pour mettre la lecture en pause, appelez la méthode `pause()` :

      ```java
      void pause() throws MediaPlayerException;
      ```

1. Utilisez le rappel de événement d’état modifié pour rechercher les erreurs ou pour effectuer d’autres actions appropriées.

   TVSDK appelle ce rappel pour `pause()` ou `play()` et transmet des informations sur le changement d’état, y compris le nouveau statut, tel que suspendu ou en cours de lecture.