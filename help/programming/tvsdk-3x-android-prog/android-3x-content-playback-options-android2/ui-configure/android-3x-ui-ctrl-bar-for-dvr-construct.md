---
description: Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge de l’enregistrement numérique (DVR) pour la diffusion VOD et la diffusion en direct. La prise en charge de l’enregistrement numérique (DVR) comprend le concept de fenêtre pouvant faire l’objet d’une recherche et le point d’activation du client.
title: Création d’une barre de contrôle améliorée pour le contrôle DVR
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Création d’une barre de contrôle améliorée pour le contrôle DVR {#construct-a-control-bar-enhanced-for-dvr}

Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge de l’enregistrement numérique (DVR) pour la diffusion VOD et la diffusion en direct. La prise en charge de l’enregistrement numérique (DVR) comprend le concept de fenêtre pouvant faire l’objet d’une recherche et le point d’activation du client.

* Pour VOD, la durée de la fenêtre pouvant faire l’objet d’une recherche correspond à la durée de la ressource entière.
* Pour la diffusion en direct en continu, la durée de la fenêtre de l’enregistreur de contenu numérique (lisible) est définie comme la période qui commence à la fenêtre de lecture en direct et se termine au point d’activation du client.

  Gardez à l’esprit les informations suivantes :

   * Le point d’activation du client est calculé en soustrayant la longueur mise en mémoire tampon de la fin de la fenêtre active.

     La durée cible est une valeur supérieure ou égale à la durée maximale d’un fragment dans le manifeste.
   * La valeur par défaut est de 10 000 ms.
   * La barre de contrôle de la lecture en direct prend en charge la réalité virtuelle en premier lieu positionnant le curseur au point d’exécution client lors du démarrage de la lecture et en affichant une région qui marque la zone où la recherche n’est pas autorisée.

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width="684"}

1. Pour mettre en oeuvre une barre de contrôle avec la prise en charge de l’enregistrement numérique (DVR), suivez les étapes de la section [Afficher une barre de défilement de recherche avec la position de lecture actuelle.](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/ui-configure/android-3x-ui-seek-scrub-bar-display.md) avec les différences suivantes :

   * Vous pouvez mettre en oeuvre une barre de contrôle qui est mappée uniquement pour la plage pouvant faire l’objet d’une recherche plutôt que pour la plage de lecture.

     Toute interaction de l’utilisateur pour la recherche peut être considérée comme sûre dans la plage pouvant faire l’objet d’une recherche.
   * Vous pouvez mettre en oeuvre une barre de contrôle qui est mappée pour la plage de lecture, mais qui affiche également la plage pouvant faire l’objet d’une recherche.

     Pour une barre de contrôle :

   1. Ajoutez une superposition à la barre de contrôle qui représente la plage de lecture.
   1. Lorsque l’utilisateur commence la recherche, vérifiez si la position de la recherche souhaitée se trouve dans la plage pouvant faire l’objet d’une recherche en utilisant `MediaPlayer.getSeekableRange`.

      Par exemple :

      ```java
      TimeRange seekableRange = _mediaPlayer.getSeekableRange(); 
      if (seekableRange.contains(desiredSeekPosition)) { 
          _mediaPlayer.seek(desiredPosition); 
      }
      ```

      Vous pouvez également choisir de rechercher le point d’entrée client à l’aide de la variable `MediaPlayer.LIVE_POINT` constante.

      ```
      mediaPlayer.seek(MediaPlayer.LIVE_POINT);
      ```
