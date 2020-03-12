---
description: Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.
seo-description: Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.
seo-title: Affiche la durée, l’heure actuelle et la durée restante de la vidéo
title: Affiche la durée, l’heure actuelle et la durée restante de la vidéo
uuid: 64536ba7-33a1-49f8-a947-5700e1e9c032
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Affiche la durée, l’heure actuelle et la durée restante de la vidéo{#display-the-duration-current-time-and-remaining-time-of-the-video}

Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.

1. Attendez que votre lecteur soit dans l’état INITIALISÉ.
1. Récupérez l’heure actuelle du curseur de lecture à l’aide de la `MediaPlayer.currentTime` propriété.

   Cette opération renvoie la position actuelle du curseur de lecture sur le plan de montage chronologique virtuel en millisecondes. Le temps est calculé par rapport au flux résolu qui peut contenir plusieurs instances de contenu alternatif, comme plusieurs publicités ou coupures publicitaires épissées dans le flux principal. Pour les flux en direct/linéaires, l’heure renvoyée se trouve toujours dans la plage de la fenêtre de lecture.

   ```
   function get currentTime():Number;
   ```

1. Récupérez la plage de lecture du flux et déterminez sa durée.
   1. Utilisez la `mediaPlayer.playbackRange` propriété pour obtenir la plage de temps de la chronologie virtuelle.

      ```
      function get playbackRange():TimeRange;
      ```

   1. Parcourez la période à l’aide de `mediacore.utils.TimeRange`.
   1. Pour déterminer la durée, soustrayez le  de la fin de la plage.

      Cela inclut la durée du contenu supplémentaire inséré dans le flux (publicités).

      Pour VOD, la plage commence toujours par zéro et la valeur de fin est égale à la somme de la durée du contenu principal et de la durée du contenu supplémentaire inséré dans le flux (publicités).

      Pour un fichier linéaire/en direct, la plage représente la plage de la fenêtre de lecture et cette plage change pendant la lecture.

      TVSDK distribue un `MediaPlayerItemEvent.ITEM_UPDATED` pour indiquer que l’élément média a été actualisé et que ses attributs (y compris la plage de lecture) ont été mis à jour.

1. Utilisez les méthodes disponibles sur la `MediaPlayer` classe et la `HSlider` classe qui est disponible publiquement dans le SDK Flex pour configurer les paramètres de barre de recherche.

1. Utilisez un minuteur pour récupérer périodiquement l’heure actuelle et mettre à jour la `SeekBar`.
