---
description: Une fois qu’un MediaPlayer a été utilisé pour lire la vidéo, vous pouvez le masquer et l’afficher de nouveau à l’aide d’une méthode TVSDK ou manuellement.
seo-description: Une fois qu’un MediaPlayer a été utilisé pour lire la vidéo, vous pouvez le masquer et l’afficher de nouveau à l’aide d’une méthode TVSDK ou manuellement.
seo-title: 'Masquer un vidéo '
title: 'Masquer un vidéo '
uuid: 7cc02bf4-41ee-4af0-98ba-df070b50b88d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Masquer un vidéo{#hide-a-video-view}

Une fois qu’un MediaPlayer a été utilisé pour lire la vidéo, vous pouvez le masquer et l’afficher de nouveau à l’aide d’une méthode TVSDK ou manuellement.

Vous devez mettre une vidéo en pause avant de l’effacer ou de la déplacer de l’affichage.
* Option 1 : Effacez l’image vidéo avec `MediaPlayer.clearVideo`&#x200B; et remplacez-la ultérieurement.
   * Mettez la vidéo en pause que vous souhaitez masquer.
   * Supprimez l’image vidéo affichée en appelant `MediaPlayer.clearVideo`.
   * Pour réinitialiser le `MediaPlayer` afin qu’il puisse être lu à nouveau, appelez `replaceCurrentResource` ou `replaceCurrentItem`.
* Option 2 : Déplacez le `MediaPlayer` hors de l’écran et déplacez-le plus tard sans avoir à le remplacer.
   * Mettez la vidéo en pause que vous souhaitez masquer.
   * Sortez le  de la scène. Par exemple :

      ```
      view.x = -300; 
      view.y = -300;
      ```

   * Pour afficher à nouveau la vidéo, déplacez le  sur la scène.
