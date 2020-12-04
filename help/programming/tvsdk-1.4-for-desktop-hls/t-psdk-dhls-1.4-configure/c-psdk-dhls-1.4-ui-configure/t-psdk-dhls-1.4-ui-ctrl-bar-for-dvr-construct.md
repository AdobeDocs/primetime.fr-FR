---
description: Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d'une fenêtre pouvant être recherchée et le point de vie du client.
seo-description: Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d'une fenêtre pouvant être recherchée et le point de vie du client.
seo-title: Construire une barre de contrôle améliorée pour le magnétoscope numérique
title: Construire une barre de contrôle améliorée pour le magnétoscope numérique
uuid: 08f943e8-90da-4860-92dd-dd289fd68cba
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---


# Construire une barre de contrôle améliorée pour DVR{#construct-a-control-bar-enhanced-for-dvr}

Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d&#39;une fenêtre pouvant être recherchée et le point de vie du client.

* Pour VOD, la longueur de la fenêtre pouvant faire l’objet d’une recherche correspond à la durée de la ressource entière.
* Pour la diffusion en continu en direct, la longueur de la fenêtre du DVR (pouvant être recherchée) est définie comme la plage de temps qui commence à la fenêtre de lecture en direct et se termine au point de lecture client.

   Le point d&#39;activation du client est calculé en soustrayant la longueur mise en mémoire tampon de l&#39;extrémité de la fenêtre active. La durée de la cible est une valeur supérieure ou égale à la durée maximale d’un fragment dans le manifeste.

   La valeur par défaut est de 1 000 ms.

   La barre de contrôle de la lecture en direct prend en charge le magnétoscope numérique en positionnant d’abord le pouce au point de lecture client lors du démarrage de la lecture et en affichant une région qui marque la zone où la recherche n’est pas autorisée.

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width=&quot;684&quot;}

1. Pour mettre en oeuvre une barre de contrôle avec prise en charge DVR, suivez les étapes pour afficher une barre de défilement de recherche, avec quelques différences mineures :

   * Vous pouvez choisir d’implémenter une barre de contrôle qui est mappée uniquement pour la plage de lecture à rechercher plutôt que pour la plage de lecture. Toute interaction de l’utilisateur pour la recherche peut être considérée comme sécurisée dans la plage recherchée.
   * Vous pouvez choisir de mettre en oeuvre une barre de contrôle mappée pour la plage de lecture, mais qui affiche également la plage de valeurs recherchée.

      Pour une barre de contrôle :
   1. Ajoutez une incrustation sur la barre de contrôle qui représente la plage de lecture.
   1. Lorsque l’utilisateur début effectuer une recherche, vérifiez si la position de recherche souhaitée se trouve dans la plage recherchée à l’aide de la propriété `MediaPlayer.seekableRange`.

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

      Vous pouvez également choisir d’accéder au point d’activation du client à l’aide de la constante `MediaPlayer.LIVE_POINT`.

      ```
      private function onSeekToLiveClick(event:MouseEvent):void { 
          _player.seek(DefaultMediaPlayer.LIVE_POINT); 
      }
      ```


