---
description: Vous pouvez ajouter un comportement TVSDK pour suspendre et lire des boutons.
title: Lecture et mise en pause d’une vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Lecture et mise en pause d’une vidéo{#play-and-pause-a-video}

Vous pouvez ajouter un comportement TVSDK pour suspendre et lire des boutons.

1. Créez un bouton de pause/lecture qui effectue les opérations suivantes.
   1. Attendez que votre lecteur soit au moins en état PRÉPARÉ .
   1. Pour démarrer la lecture, appelez la méthode de lecture TVSDK :

      ```
      function play():void;
      ```

   1. Pour mettre la lecture en pause, appelez la méthode pause TVSDK :

      ```
      function pause():void;
      ```

1. Utilisez le rappel pour la variable `MediaPlayerStatusChangeEvent.STATUS_CHANGED` pour rechercher des erreurs ou pour prendre d’autres mesures appropriées.

   TVSDK appelle ce rappel lorsque la méthode pause ou play est appelée. TVSDK transmet des informations sur le changement d’état dans le rappel, y compris sur le nouvel état, comme PAUSED ou PLAYING.
