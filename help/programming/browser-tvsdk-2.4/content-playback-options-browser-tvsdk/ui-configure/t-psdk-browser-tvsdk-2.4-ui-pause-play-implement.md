---
description: Vous pouvez ajouter le comportement du navigateur TVSDK pour mettre en pause et lire les boutons.
seo-description: Vous pouvez ajouter le comportement du navigateur TVSDK pour mettre en pause et lire les boutons.
seo-title: Lecture et mise en pause d’une vidéo
title: Lecture et mise en pause d’une vidéo
uuid: 4053ea9e-6b74-41e9-ad04-087ad13e3698
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Lecture et mise en pause d’une vidéo{#play-and-pause-a-video}

Vous pouvez ajouter le comportement du navigateur TVSDK pour mettre en pause et lire les boutons.

1. Créez un bouton Pause/Lecture qui effectue les opérations suivantes.
   1. Attendez que votre joueur soit dans l&#39;état PRÉPARÉ.
   1. Pour  lecture, appelez la méthode de lecture du navigateur TVSDK :

      ```js
      play() → {AdobePSDK.PSDKErrorCode.SUCCESS}
      ```

   1. Pour mettre la lecture en pause, appelez la méthode de mise en pause du navigateur TVSDK :

      ```java
      void pause() throws IllegalStateException;
      ```

1. Ecoutez le `AdobePSDK.MediaPlayerStatusChangeEvent` à rechercher les erreurs ou à prendre d’autres mesures appropriées.

   Le navigateur TVSDK déclenche ce lorsque des méthodes pause ou play sont appelées et transmet des informations sur l’objet , y compris le nouvel état, tel que `MediaPlayerStatus.PLAYING` ou `MediaPlayerStatus.PAUSED`.

