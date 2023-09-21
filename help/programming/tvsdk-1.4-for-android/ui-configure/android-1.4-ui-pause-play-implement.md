---
description: Vous pouvez ajouter un comportement TVSDK pour suspendre et lire des boutons.
title: Lecture et mise en pause d’une vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Lecture et mise en pause d’une vidéo{#play-and-pause-a-video}

Vous pouvez ajouter un comportement TVSDK pour suspendre et lire des boutons.

1. Créez un bouton de pause/lecture qui effectue les opérations suivantes.
   1. Attendez que votre lecteur soit à au moins l’état PRÉPARÉ .
   1. Pour démarrer la lecture, appelez la méthode de lecture TVSDK :

      ```java
      void play() throws IllegalStateException;
      ```

   1. Pour mettre la lecture en pause, appelez la méthode pause TVSDK :

      ```java
      void pause() throws IllegalStateException;
      ```

1. Utilisez la variable `MediaPlayer.PlaybackEventListener.onStateChanged` rappel pour rechercher des erreurs ou pour prendre d’autres mesures appropriées.

   TVSDK appelle ce rappel lorsque la méthode pause ou play est appelée. TVSDK transmet des informations sur le changement d’état dans le rappel, y compris sur le nouvel état, comme PAUSED ou PLAYING.
