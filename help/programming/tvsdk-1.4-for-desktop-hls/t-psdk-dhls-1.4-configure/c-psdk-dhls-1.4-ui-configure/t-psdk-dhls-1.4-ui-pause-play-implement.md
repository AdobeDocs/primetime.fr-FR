---
description: Vous pouvez ajouter un comportement TVSDK pour mettre en pause et lire des boutons.
title: Lecture et mise en pause d’une vidéo
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# Lecture et mise en pause d’une vidéo {#play-and-pause-a-video}

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

1. Utilisez le rappel du événement `MediaPlayerStatusChangeEvent.STATUS_CHANGED` pour rechercher les erreurs ou pour prendre d&#39;autres mesures appropriées.

   TVSDK appelle ce rappel lorsque la méthode pause ou play est appelée. TVSDK transmet des informations sur le changement d’état dans le rappel, y compris le nouveau statut, tel que PAUSED ou PLAYING.
