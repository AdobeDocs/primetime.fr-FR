---
description: Le sous-titrage codé affiche la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que la visionneuse est difficile à entendre.
title: Sélectionner un suivi de légende actuel parmi les pistes disponibles
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Sélectionner un suivi de légende actuel parmi les pistes disponibles{#select-a-current-caption-track-from-among-available-tracks}

Vous pouvez sélectionner un suivi dans une liste de suivi de sous-titres actuellement disponibles. Cela devient le suivi actuel, qui s’affiche lorsque la visibilité est activée. Il se peut que certaines pistes ne soient pas disponibles initialement. Par conséquent, écoutez l’événement qui indique que d’autres sont devenues disponibles.

>[!TIP]
>
>Les sous-titres codés sont toujours activés. Tous les suivi de sous-titres fermés par défaut sont considérés comme présents. Les pistes par défaut (comme CC1-CC4, CS1-CS6) sont énumérées dans `ClosedCaptionsTrack.DefaultCCTypes`. Lorsque la lecture démarre, TVSDK recherche l’activité sur l’un de ces canaux. S’il détecte une activité, il définit la variable `isActive` pour ce suivi et distribue la méthode `MediaPlayer.PlaybackEventListener.onUpdated` .

1. Attendez que le lecteur multimédia soit au moins à l’état PRÉPARÉ .
1. Prêtez attention aux événements suivants :

   * `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: la liste initiale des pistes de sous-titres est disponible.

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
           mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track); 
           selectedClosedCaptionsIndex = i; 
       } 
   }
   ```

1. Implémentez un écouteur pour l’événement qui indique que d’autres pistes sont disponibles. Lorsque TVSDK distribue l’événement, récupérez la liste actuelle des pistes disponibles.

   Récupérez la liste chaque fois que l’événement se produit pour vous assurer que vous disposez toujours de la liste la plus récente.
