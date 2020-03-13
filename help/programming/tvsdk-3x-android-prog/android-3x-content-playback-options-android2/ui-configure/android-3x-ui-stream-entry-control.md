---
description: Par défaut, lors du démarrage de la lecture, le de médias VOD  à 0 et le de médias en direct  au point d’accès client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
seo-description: Par défaut, lors du démarrage de la lecture, le de médias VOD  à 0 et le de médias en direct  au point d’accès client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
seo-title: Entrer un flux à un moment spécifique
title: Entrer un flux à un moment spécifique
uuid: b315a967-77ad-4352-8a32-f228704d4b20
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# Entrer un flux à un moment spécifique {#enter-a-stream-at-a-specific-time}

Par défaut, lors du démarrage de la lecture, le de médias VOD  à 0 et le de médias en direct  au point d’accès client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.

1. Passe une position à `MediaPlayer.prepareToPlay`.

   TVSDK considère la position donnée comme le point de départ de la ressource et aucune opération de recherche n’est requise. Si la position n’est pas comprise dans la plage recherchée, TVSDK utilise la position par défaut. Pour plus d’informations, voir [Chargement d’une ressource multimédia dans le lecteur](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md)multimédia.

   Par exemple :

   ```java
   long desiredPostion = // TODO : choose a value; 
   @Override 
   public void onStatusChanged(MediaPlayerStatusChangedEvent statusChangedEvent) {   
       switch (statusChangedEvent.getStatus()) { 
           case INITIALIZED: 
               _mediaPlayer.prepareToPlay(desiredPosition); 
               break; 
           case PREPARING: 
               showBufferingSpinner(); 
               break; 
       } 
   }
   ```
