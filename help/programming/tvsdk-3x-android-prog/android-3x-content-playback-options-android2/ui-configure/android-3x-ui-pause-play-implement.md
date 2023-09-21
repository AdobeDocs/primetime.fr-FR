---
description: Vous pouvez ajouter des boutons de pause et de lecture pour suspendre ou lire votre vidéo.
title: Lecture et mise en pause d’une vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Lecture et mise en pause d’une vidéo {#play-and-pause-a-video}

Vous pouvez ajouter des boutons de pause et de lecture pour suspendre ou lire votre vidéo.

1. Pour créer un bouton de pause ou de lecture :
   1. Attendez que le lecteur soit au moins à l’état préparé.
   1. Pour démarrer la lecture, appelez la fonction `play` method :

      ```java
      void play() throws MediaPlayerException;
      ```

   1. Pour mettre la lecture en pause, appelez la fonction `pause()` method :

      ```java
      void pause() throws MediaPlayerException;
      ```

1. Utilisez le rappel d’événement status changed pour rechercher des erreurs ou prendre d’autres mesures appropriées.

   TVSDK appelle ce rappel pour `pause()` ou `play()` et transmet des informations sur le changement d’état, y compris le nouvel état, comme en pause ou en lecture.
