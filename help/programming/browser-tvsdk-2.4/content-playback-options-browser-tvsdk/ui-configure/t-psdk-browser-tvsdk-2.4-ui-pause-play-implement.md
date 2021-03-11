---
description: Vous pouvez ajouter le comportement du navigateur TVSDK pour mettre en pause et lire les boutons.
title: Lecture et mise en pause d’une vidéo
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Lecture et mise en pause d’une vidéo {#play-and-pause-a-video}

Vous pouvez ajouter le comportement du navigateur TVSDK pour mettre en pause et lire les boutons.

1. Créez un bouton Pause/Lecture qui effectue les opérations suivantes.
   1. Attendez que votre lecteur soit au moins à l’état PRÉPARÉ.
   1. Pour début la lecture, appelez la méthode de lecture du navigateur TVSDK :

      ```js
      play() → {AdobePSDK.PSDKErrorCode.SUCCESS}
      ```

   1. Pour mettre la lecture en pause, appelez la méthode de mise en pause du navigateur TVSDK :

      ```java
      void pause() throws IllegalStateException;
      ```

1. Prêtez attention au événement `AdobePSDK.MediaPlayerStatusChangeEvent` pour rechercher les erreurs ou prendre d&#39;autres mesures appropriées.

   Le navigateur TVSDK déclenche ce événement lorsque des méthodes pause ou play sont appelées et transmet des informations sur l’objet événement, y compris le nouvel état, tel que `MediaPlayerStatus.PLAYING` ou `MediaPlayerStatus.PAUSED`.

