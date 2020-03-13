---
description: Le sous-titrage affiche la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.
seo-description: Le sous-titrage affiche la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.
seo-title: Sélectionner une piste de sous-titrage parmi les pistes disponibles
title: Sélectionner une piste de sous-titrage parmi les pistes disponibles
uuid: 637a70c9-9bef-4b13-8b1f-62f22f983e80
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Sélectionner une piste de sous-titrage parmi les pistes disponibles{#select-a-current-caption-track-from-among-available-tracks}

Vous pouvez sélectionner une piste dans un de pistes de sous-titrage actuellement disponibles. Il devient la piste actuelle, qui s’affiche lorsque la visibilité est activée. Il se peut que certaines pistes ne soient pas disponibles au départ. Écoutez donc le  qui indique que d&#39;autres sont devenues disponibles.

>[!TIP]
>
>Les sous-titres sont toujours activés. Toutes les pistes de sous-titrage codé par défaut sont considérées comme présentes. Les pistes par défaut (CC1-CC4, CS1-CS6, par exemple) sont énumérées dans `ClosedCaptionsTrack.DefaultCCTypes`. Lorsque la lecture commence, TVSDK recherche   sur l’un de ces . S’il trouve  , il définit la `isActive` méthode de cette piste et distribue le `MediaPlayer.PlaybackEventListener.onUpdated` .

1. Attendez que le lecteur de médias soit au moins à l’état PRÉPARÉ.
1. Ecoutez ces  :

   * `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: Le  initial des pistes de sous-titrage est disponible

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
}}

```
1. Implement a listener for the event that indicates that more tracks are available. When TVSDK dispatches the event, retrieve the current list of available tracks.

Retrieve the list each time that the event occurs to ensure that you always have the most current list.

