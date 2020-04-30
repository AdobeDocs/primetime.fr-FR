---
description: Vous pouvez ajouter un comportement TVSDK pour mettre en pause et lire des boutons.
seo-description: Vous pouvez ajouter un comportement TVSDK pour mettre en pause et lire des boutons.
seo-title: Lecture et mise en pause d’une vidéo
title: Lecture et mise en pause d’une vidéo
uuid: 04b3b23f-5ef1-4cc4-a22f-f6ffa9cefce5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Lecture et mise en pause d’une vidéo{#play-and-pause-a-video}

Vous pouvez ajouter un comportement TVSDK pour mettre en pause et lire des boutons.

1. Créez un bouton Pause/Lecture qui effectue les opérations suivantes.
   1. Attendez que votre lecteur soit au moins en état PRÉPARÉ.
   1. Pour début la lecture, appelez la méthode de lecture TVSDK :

      ```
      function play():void;
      ```

   1. Pour mettre la lecture en pause, appelez la méthode de mise en pause TVSDK :

      ```
      function pause():void;
      ```

1. Utilisez le rappel du `MediaPlayerStatusChangeEvent.STATUS_CHANGED` événement pour rechercher les erreurs ou pour prendre d’autres mesures appropriées.

   TVSDK appelle ce rappel lorsque la méthode pause ou play est appelée. TVSDK transmet des informations sur le changement d’état dans le rappel, y compris le nouveau statut, tel que PAUSED ou PLAYING.
