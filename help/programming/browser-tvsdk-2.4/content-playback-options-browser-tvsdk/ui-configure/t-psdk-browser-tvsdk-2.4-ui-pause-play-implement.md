---
description: Vous pouvez ajouter le comportement Browser TVSDK pour suspendre et lire les boutons.
title: Lecture et mise en pause d’une vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Lecture et mise en pause d’une vidéo{#play-and-pause-a-video}

Vous pouvez ajouter le comportement Browser TVSDK pour suspendre et lire les boutons.

1. Créez un bouton de pause/lecture qui effectue les opérations suivantes.
   1. Attendez que votre lecteur soit à au moins l’état PRÉPARÉ .
   1. Pour démarrer la lecture, appelez la méthode de lecture Browser TVSDK :

      ```js
      play() → {AdobePSDK.PSDKErrorCode.SUCCESS}
      ```

   1. Pour mettre la lecture en pause, appelez la méthode de pause Browser TVSDK :

      ```java
      void pause() throws IllegalStateException;
      ```

1. Écoute de la `AdobePSDK.MediaPlayerStatusChangeEvent` pour rechercher des erreurs ou pour prendre d’autres mesures appropriées.

   Le TVSDK du navigateur déclenche cet événement lorsque des méthodes de mise en pause ou de lecture sont appelées et transmet des informations sur l’objet d’événement, y compris le nouvel état, tel que `MediaPlayerStatus.PLAYING` ou `MediaPlayerStatus.PAUSED`.
