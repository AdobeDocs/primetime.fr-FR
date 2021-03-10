---
description: Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d'une fenêtre pouvant être recherchée et le point de vie du client.
title: Construire une barre de contrôle améliorée pour le magnétoscope numérique
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# Construire une barre de contrôle améliorée pour DVR {#construct-a-control-bar-enhanced-for-dvr}

Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d&#39;une fenêtre pouvant être recherchée et le point de vie du client.

* Pour VOD, la longueur de la fenêtre pouvant faire l’objet d’une recherche correspond à la durée de la ressource entière.
* Pour la diffusion en flux continu en direct, la longueur de la fenêtre du DVR (pouvant être recherchée) est définie comme la plage de temps qui s’début à la fenêtre de lecture en direct et se termine au point de lecture client.

   Rappelez-vous des informations suivantes :

   * Le point d&#39;activation du client est calculé en soustrayant la longueur mise en mémoire tampon de l&#39;extrémité de la fenêtre active.

      La durée de la cible est une valeur supérieure ou égale à la durée maximale d’un fragment dans le manifeste.
   * La valeur par défaut est de 1 000 ms.
   * La barre de contrôle de la lecture en direct prend en charge le magnétoscope numérique en positionnant d’abord le pouce au point de lecture client lors du démarrage de la lecture et en affichant une région qui marque la zone où la recherche n’est pas autorisée.

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width=&quot;684&quot;}

1. Pour mettre en oeuvre une barre de contrôle avec prise en charge du DVR, suivez les étapes décrites dans [Afficher une barre de défilement de recherche avec la position de lecture actuelle.](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/ui-configure/android-3x-ui-seek-scrub-bar-display.md) avec les différences suivantes :

   * Vous pouvez mettre en oeuvre une barre de contrôle qui est mappée uniquement pour la plage recherchée et non pour la plage de lecture.

      Toute interaction de l’utilisateur pour la recherche peut être considérée comme sécurisée dans la plage recherchée.
   * Vous pouvez mettre en oeuvre une barre de contrôle mappée pour la plage de lecture, mais qui affiche également la plage de valeurs recherchée.

      Pour une barre de contrôle :
   1. Ajoutez une incrustation sur la barre de contrôle qui représente la plage de lecture.
   1. Lorsque l&#39;utilisateur début effectuer une recherche, vérifiez si la position de recherche souhaitée se trouve dans la plage recherchée à l&#39;aide de `MediaPlayer.getSeekableRange`.

      Par exemple :

      ```java
      TimeRange seekableRange = _mediaPlayer.getSeekableRange(); 
      if (seekableRange.contains(desiredSeekPosition)) { 
          _mediaPlayer.seek(desiredPosition); 
      }
      ```

      Vous pouvez également choisir d’accéder au point d’activation du client à l’aide de la constante `MediaPlayer.LIVE_POINT`.

      ```
      mediaPlayer.seek(MediaPlayer.LIVE_POINT);
      ```
