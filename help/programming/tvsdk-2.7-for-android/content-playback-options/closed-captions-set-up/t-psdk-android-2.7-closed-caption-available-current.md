---
description: Vous pouvez sélectionner une piste dans un de pistes de sous-titrage actuellement disponibles. Il devient la piste actuelle, qui s’affiche lorsque la visibilité est activée. Il se peut que certaines pistes ne soient pas disponibles au départ. Écoutez donc le  qui indique que d'autres sont devenues disponibles.
seo-description: Vous pouvez sélectionner une piste dans un de pistes de sous-titrage actuellement disponibles. Il devient la piste actuelle, qui s’affiche lorsque la visibilité est activée. Il se peut que certaines pistes ne soient pas disponibles au départ. Écoutez donc le  qui indique que d'autres sont devenues disponibles.
seo-title: Sélectionner une piste de sous-titrage parmi les pistes disponibles
title: Sélectionner une piste de sous-titrage parmi les pistes disponibles
uuid: d582779a-2789-4e2a-85f6-1a0b9b847382
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Sélectionner une piste de sous-titrage parmi les pistes disponibles {#select-a-current-caption-track-from-among-available-tracks}

Vous pouvez sélectionner une piste dans un de pistes de sous-titrage actuellement disponibles. Il devient la piste actuelle, qui s’affiche lorsque la visibilité est activée. Il se peut que certaines pistes ne soient pas disponibles au départ. Écoutez donc le  qui indique que d&#39;autres sont devenues disponibles.

1. Attendez que le lecteur de médias soit au moins dans son `PREPARED` état.
1. Ecoutez ces  :

   * `MediaPlayerEvent.STATUS_CHANGED` avec le statut `MediaPlayerStatus.INITIALIZED`: Le  initial des pistes de sous-titrage est disponible.

1. Obtenez un  de toutes les pistes de sous-titrage actuellement disponibles.

   Par exemple :

   ```java
   List<ClosedCaptionsTrack> ccTracks = 
     mediaPlayer.getCurrentItem().getClosedCaptionsTracks();
   ```

1. Sélectionnez une piste disponible pour être la piste actuelle.

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

1. Implémentez un écouteur pour le qui indique que davantage de pistes sont disponibles. Lorsque TVSDK distribue le , récupérez le actuel des pistes disponibles.

   Récupérez le  chaque fois que le  se produit pour vous assurer que vous disposez toujours de l’ la plus récente.