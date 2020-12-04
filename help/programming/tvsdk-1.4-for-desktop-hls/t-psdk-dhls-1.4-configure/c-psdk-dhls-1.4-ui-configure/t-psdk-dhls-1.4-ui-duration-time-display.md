---
description: Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.
seo-description: Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.
seo-title: Affiche la durée, l’heure actuelle et l’heure restante de la vidéo.
title: Affiche la durée, l’heure actuelle et l’heure restante de la vidéo.
uuid: 64536ba7-33a1-49f8-a947-5700e1e9c032
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Affiche la durée, l’heure actuelle et l’heure restante de la vidéo{#display-the-duration-current-time-and-remaining-time-of-the-video}

Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.

1. Attendez que votre lecteur soit dans l’état INITIALISÉ.
1. Récupérez l’heure actuelle du curseur de lecture à l’aide de la propriété `MediaPlayer.currentTime`.

   Cette opération renvoie la position actuelle du curseur de lecture sur le plan de montage chronologique virtuel en millisecondes. Le temps est calculé par rapport au flux résolu qui peut contenir plusieurs instances de contenu alternatif, telles que plusieurs publicités ou coupures publicitaires épissées dans le flux principal. Pour les flux en direct/linéaires, l’heure renvoyée se trouve toujours dans la plage de la fenêtre de lecture.

   ```
   function get currentTime():Number;
   ```

1. Récupérez la plage de lecture du flux et déterminez sa durée.
   1. Utilisez la propriété `mediaPlayer.playbackRange` pour obtenir la plage de temps de la chronologie virtuelle.

      ```
      function get playbackRange():TimeRange;
      ```

   1. Analyse de la période à l&#39;aide de `mediacore.utils.TimeRange`.
   1. Pour déterminer la durée, soustrayez le début de la fin de la plage.

      Cela inclut la durée du contenu supplémentaire qui est inséré dans le flux (publicités).

      Pour VOD, la plage commence toujours par zéro et la valeur finale est égale à la somme de la durée du contenu principal et de la durée du contenu supplémentaire inséré dans le flux (publicités).

      Pour un fichier linéaire/vivant, la plage représente la plage de la fenêtre de lecture et cette plage change pendant la lecture.

      TVSDK distribue un événement `MediaPlayerItemEvent.ITEM_UPDATED` pour indiquer que l’élément média a été actualisé et que ses attributs (y compris la plage de lecture) ont été mis à jour.

1. Utilisez les méthodes disponibles dans les classes `MediaPlayer` et `HSlider` disponibles publiquement dans le SDK Flex pour configurer les paramètres de barre de recherche.

1. Utilisez un minuteur pour récupérer périodiquement l&#39;heure actuelle et mettre à jour `SeekBar`.
