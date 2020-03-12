---
description: Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d'une fenêtre pouvant être recherchée et le point de vie du client.
seo-description: Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d'une fenêtre pouvant être recherchée et le point de vie du client.
seo-title: Construire une barre de contrôle améliorée pour le magnétoscope numérique
title: Construire une barre de contrôle améliorée pour le magnétoscope numérique
uuid: 08f943e8-90da-4860-92dd-dd289fd68cba
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Construire une barre de contrôle améliorée pour le magnétoscope numérique{#construct-a-control-bar-enhanced-for-dvr}

Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d&#39;une fenêtre pouvant être recherchée et le point de vie du client.

* Pour VOD, la longueur de la fenêtre pouvant faire l’objet d’une recherche correspond à la durée de la ressource entière.
* Pour la diffusion en direct, la longueur de la fenêtre du DVR (consultable) est définie comme la plage de temps qui commence à la fenêtre de lecture en direct et se termine au point de diffusion client.

   Le point d’activation du client est calculé en soustrayant la longueur mise en mémoire tampon de l’extrémité de la fenêtre active. La durée  du est une valeur supérieure ou égale à la durée maximale d’un fragment dans le manifeste.

   La valeur par défaut est de 1 000 ms.

   La barre de contrôle de la lecture en direct prend en charge le magnétoscope numérique en positionnant d’abord le curseur au point de lecture client lors du démarrage de la lecture et en affichant une région qui marque la zone où la recherche n’est pas autorisée.

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width=&quot;684&quot;}

1. Pour mettre en oeuvre une barre de contrôle avec prise en charge DVR, procédez comme suit pour afficher une barre de défilement de recherche, avec quelques différences mineures :

   * Vous pouvez choisir de mettre en oeuvre une barre de contrôle mappée uniquement pour la plage de lecture qui peut être recherchée au lieu de la plage de lecture. Toute interaction utilisateur pour la recherche peut être considérée comme sûre dans la plage recherchée.
   * Vous pouvez choisir de mettre en oeuvre une barre de contrôle mappée pour la plage de lecture, mais qui affiche également la plage pouvant faire l’objet d’une recherche.

      Pour une barre de contrôle :
   1. Ajouter d’une incrustation sur la barre de contrôle qui représente la plage de lecture.
   1. Lorsque l’utilisateur  effectuer une recherche, vérifiez si la position de recherche souhaitée se trouve dans la plage recherchée à l’aide de la `MediaPlayer.seekableRange` propriété.

      Par exemple :

      ```
      var desiredPosition:Number = // TODO : choose a value 
      
      private function onStatusChange(event:MediaPlayerStatusChangeEvent):void { 
          switch(event.status) { 
              case MediaPlayerStatus.PREPARED: 
                  _mediaPlayer.prepareToPlay(desiredPosition); 
          } 
      }
      ```

      Vous pouvez également choisir de rechercher le point de vie du client à l’aide de la `MediaPlayer.LIVE_POINT` constante.

      ```
      private function onSeekToLiveClick(event:MouseEvent):void { 
          _player.seek(DefaultMediaPlayer.LIVE_POINT); 
      }
      ```


