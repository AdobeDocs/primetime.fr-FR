---
description: Une fois qu’une vue MediaPlayer a été utilisée pour lire une vidéo, vous pouvez la masquer et l’afficher à nouveau à l’aide d’une méthode TVSDK ou manuellement.
title: Masquage d’un affichage vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Masquage d’un affichage vidéo{#hide-a-video-view}

Une fois qu’une vue MediaPlayer a été utilisée pour lire une vidéo, vous pouvez la masquer et l’afficher à nouveau à l’aide d’une méthode TVSDK ou manuellement.

Vous devez suspendre une vidéo avant de l’effacer ou de la déplacer à partir de l’affichage.
* Option 1 : effacer la image vidéo avec `MediaPlayer.clearVideo`&#x200B; et remplacez le cadre ultérieurement.
   * Mettez la vidéo en pause à masquer.
   * Supprimez la image vidéo affichée en appelant `MediaPlayer.clearVideo`.
   * Pour réinitialiser la variable `MediaPlayer` pour qu’il puisse être relu, appelez `replaceCurrentResource` ou `replaceCurrentItem`.
* Option 2 : déplacez le `MediaPlayer` affichez l’écran et revenez-le plus tard sans avoir à le remplacer.
   * Mettez la vidéo en pause à masquer.
   * Déplacez la vue hors de la scène. Par exemple :

     ```
     view.x = -300; 
     view.y = -300;
     ```

   * Pour afficher à nouveau la vidéo, déplacez la vue vers la scène.
