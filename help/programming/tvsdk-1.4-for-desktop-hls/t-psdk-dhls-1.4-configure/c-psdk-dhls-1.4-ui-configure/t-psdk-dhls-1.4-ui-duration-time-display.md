---
description: Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.
title: Afficher la durée, l’heure actuelle et l’heure restante de la vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Afficher la durée, l’heure actuelle et l’heure restante de la vidéo{#display-the-duration-current-time-and-remaining-time-of-the-video}

Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.

1. Attendez que votre lecteur soit à l’état INITIALISÉ .
1. Récupérez l’heure actuelle du curseur de lecture à l’aide de la variable `MediaPlayer.currentTime` .

   Cette opération renvoie la position actuelle du curseur de lecture sur la chronologie virtuelle en millisecondes. Le temps est calculé par rapport au flux résolu qui peut contenir plusieurs instances de contenu alternatif, comme plusieurs publicités ou coupures publicitaires répliquées dans le flux principal. Pour les flux en direct/linéaires, l’heure renvoyée se trouve toujours dans la plage de la fenêtre de lecture.

   ```
   function get currentTime():Number;
   ```

1. Récupérez la plage de lecture de la diffusion et déterminez la durée.
   1. Utilisez la variable `mediaPlayer.playbackRange` pour obtenir la plage temporelle de la chronologie virtuelle.

      ```
      function get playbackRange():TimeRange;
      ```

   1. Parcourez la période à l’aide de `mediacore.utils.TimeRange`.
   1. Pour déterminer la durée, soustrayez le début de la fin de la période.

      Cela inclut la durée du contenu supplémentaire inséré dans le flux (publicités).

      Pour VOD, la plage commence toujours par zéro et la valeur de fin est égale à la somme de la durée du contenu principal et des durées du contenu supplémentaire inséré dans le flux (publicités).

      Pour une ressource linéaire/vivante, la plage représente la plage de la fenêtre de lecture, et cette plage change pendant la lecture.

      TVSDK distribue une `MediaPlayerItemEvent.ITEM_UPDATED` pour indiquer que l’élément multimédia a été actualisé et que ses attributs (y compris la plage de lecture) ont été mis à jour.

1. Utilisez les méthodes disponibles dans la variable `MediaPlayer` et la variable `HSlider` qui est disponible publiquement dans le SDK Flex pour configurer les paramètres de barre de recherche.

1. Utilisez un minuteur pour récupérer périodiquement l’heure actuelle et mettre à jour la variable `SeekBar`.
