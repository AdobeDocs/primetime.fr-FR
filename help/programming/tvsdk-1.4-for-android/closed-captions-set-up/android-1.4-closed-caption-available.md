---
description: Le sous-titrage permet d’afficher la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.
title: Sélectionner une piste de sous-titrage actuelle parmi les pistes disponibles
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 1%

---


# Sélectionnez une piste de légende actuelle parmi les pistes disponibles{#select-a-current-caption-track-from-among-available-tracks}

Vous pouvez sélectionner une piste à partir d’une liste de pistes de sous-titres actuellement disponibles. Cela devient la piste actuelle, qui s’affiche lorsque la visibilité est activée. Certaines pistes ne sont peut-être pas disponibles au départ, alors écoutez le événement qui indique que d&#39;autres sont devenues disponibles.

>[!TIP]
>
>Les légendes fermées sont toujours activées. Toutes les pistes de sous-titrage par défaut sont considérées comme présentes. Les pistes par défaut (telles que CC1-CC4, CS1-CS6) sont énumérées dans `ClosedCaptionsTrack.DefaultCCTypes`. Lorsque la lecture commence, TVSDK recherche l’activité sur l’un de ces canaux. S&#39;il détecte l&#39;activité, il définit la méthode `isActive` pour cette piste et distribue le événement `MediaPlayer.PlaybackEventListener.onUpdated`.

1. Attendez que le lecteur multimédia soit au moins à l’état PRÉPARÉ.
1. Prêtez attention aux événements suivants :

   * `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: La liste initiale des pistes de sous-titrage est disponible

1. Obtenez une liste de toutes les pistes de sous-titrage actuellement disponibles.

   Par exemple :

   ```java
   List<ClosedCaptionsTrack> ccTracks = 
         mediaPlayer.getCurrentItem().getClosedCaptionsTracks();
   ```

1. Sélectionnez une piste disponible pour être la piste en cours.

   Par exemple :

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

1. Implémentez un écouteur pour le événement qui indique que davantage de pistes sont disponibles. Lorsque TVSDK distribue le événement, récupérez la liste actuelle des pistes disponibles.

   Récupérez la liste chaque fois que le événement se produit pour vous assurer que vous disposez toujours de la liste la plus récente.
