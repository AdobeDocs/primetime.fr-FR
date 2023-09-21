---
description: Vous pouvez sélectionner un suivi dans une liste de suivi de sous-titres actuellement disponibles. Cela devient le suivi actuel, qui s’affiche lorsque la visibilité est activée. Il se peut que certaines pistes ne soient pas disponibles initialement. Par conséquent, écoutez l’événement qui indique que d’autres sont devenues disponibles.
title: Sélectionner un suivi de légende actuel parmi les pistes disponibles
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Sélectionner un suivi de légende actuel parmi les pistes disponibles {#select-a-current-caption-track-from-among-available-tracks}

Vous pouvez sélectionner un suivi dans une liste de suivi de sous-titres actuellement disponibles. Cela devient le suivi actuel, qui s’affiche lorsque la visibilité est activée. Il se peut que certaines pistes ne soient pas disponibles initialement. Par conséquent, écoutez l’événement qui indique que d’autres sont devenues disponibles.

1. Attendez que le lecteur multimédia se trouve au moins dans la balise `PREPARED` statut.
1. Prêtez attention aux événements suivants :

   * `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZED`: la liste initiale des suivis de sous-titres est disponible.

1. Obtenez une liste de tous les suivi de sous-titres actuellement disponibles.

   Par exemple :

   ```java
   List<ClosedCaptionsTrack> ccTracks = 
     mediaPlayer.getCurrentItem().getClosedCaptionsTracks();
   ```

1. Sélectionnez une piste disponible pour la suivi en cours.

   Par exemple :

   ```java
   // Select the initial CC track. 
   for (int i = 0; i < ccTracks.size(); i++) { 
       ClosedCaptionsTrack track = ccTracks.get(i); 
       if (track.getName().equals(INITIAL_CC_TRACK)) {
        <b>mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track);</b> 
             selectedClosedCaptionsIndex = i; 
       } 
   }
   ```

1. Implémentez un écouteur pour l’événement qui indique que d’autres pistes sont disponibles. Lorsque TVSDK distribue l’événement, récupérez la liste actuelle des pistes disponibles.

   Récupérez la liste chaque fois que l’événement se produit pour vous assurer que vous disposez toujours de la liste la plus récente.
