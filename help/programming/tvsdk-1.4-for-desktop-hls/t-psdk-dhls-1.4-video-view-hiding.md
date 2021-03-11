---
description: Une fois qu’une vue MediaPlayer a été utilisée pour lire une vidéo, vous pouvez la masquer et l’afficher de nouveau à l’aide d’une méthode TVSDK ou manuellement.
title: Masquer une vue vidéo
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 1%

---


# Masquer une vue vidéo{#hide-a-video-view}

Une fois qu’une vue MediaPlayer a été utilisée pour lire une vidéo, vous pouvez la masquer et l’afficher de nouveau à l’aide d’une méthode TVSDK ou manuellement.

Vous devez mettre une vidéo en pause avant de la supprimer ou de la déplacer de l’affichage.
* Option 1 : Effacez l’image vidéo avec `MediaPlayer.clearVideo` &#x200B; et remplacez-la ultérieurement.
   * Mettez la vidéo en pause que vous souhaitez masquer.
   * Supprimez la trame vidéo affichée en appelant `MediaPlayer.clearVideo`.
   * Pour réinitialiser le `MediaPlayer` afin qu&#39;il puisse être relu, appelez `replaceCurrentResource` ou `replaceCurrentItem`.
* Option 2 : Déplacez la vue `MediaPlayer` hors de l&#39;écran et déplacez-la plus tard sans avoir à la remplacer.
   * Mettez la vidéo en pause que vous souhaitez masquer.
   * Sortez la vue de la scène. Par exemple :

      ```
      view.x = -300; 
      view.y = -300;
      ```

   * Pour afficher à nouveau la vidéo, replacez la vue sur la scène.
