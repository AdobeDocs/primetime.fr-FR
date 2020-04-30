---
description: Vous pouvez sélectionner une piste à partir d’une liste de pistes de sous-titres actuellement disponibles. Cela devient la piste actuelle, qui s’affiche lorsque la visibilité est activée. Certaines pistes ne sont peut-être pas disponibles au départ, alors écoutez le événement qui indique que d'autres sont devenues disponibles.
seo-description: Vous pouvez sélectionner une piste à partir d’une liste de pistes de sous-titres actuellement disponibles. Cela devient la piste actuelle, qui s’affiche lorsque la visibilité est activée. Certaines pistes ne sont peut-être pas disponibles au départ, alors écoutez le événement qui indique que d'autres sont devenues disponibles.
seo-title: Sélectionner une piste de sous-titrage actuelle parmi les pistes disponibles
title: Sélectionner une piste de sous-titrage actuelle parmi les pistes disponibles
uuid: d582779a-2789-4e2a-85f6-1a0b9b847382
translation-type: tm+mt
source-git-commit: ''

---


# Sélectionner une piste de sous-titrage actuelle parmi les pistes disponibles {#select-a-current-caption-track-from-among-available-tracks}

Vous pouvez sélectionner une piste à partir d’une liste de pistes de sous-titres actuellement disponibles. Cela devient la piste actuelle, qui s’affiche lorsque la visibilité est activée. Certaines pistes ne sont peut-être pas disponibles au départ, alors écoutez le événement qui indique que d&#39;autres sont devenues disponibles.

1. Attendez que le lecteur de médias soit au moins en `PREPARED` état.
1. Prêtez attention aux événements suivants :

   * `MediaPlayerEvent.STATUS_CHANGED` avec le statut `MediaPlayerStatus.INITIALIZED`: La liste initiale des pistes de sous-titrage est disponible.

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
       <b>mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track);</b> 
             selectedClosedCaptionsIndex = i; 
       } 
   }
   ```

1. Implémentez un écouteur pour le événement qui indique que davantage de pistes sont disponibles. Lorsque TVSDK distribue le événement, récupérez la liste actuelle des pistes disponibles.

   Récupérez la liste chaque fois que le événement se produit pour vous assurer que vous disposez toujours de la liste la plus récente.