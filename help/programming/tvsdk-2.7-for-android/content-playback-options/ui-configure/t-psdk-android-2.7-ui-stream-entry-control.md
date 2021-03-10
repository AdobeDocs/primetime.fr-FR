---
description: Par défaut, lors du démarrage de la lecture, les médias VOD sont débuts à 0 et les débuts de médias en direct au point d’accès client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
title: Entrer un flux à un moment donné
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 1%

---


# Entrer un flux à un moment spécifique {#enter-a-stream-at-a-specific-time}

Par défaut, lors du démarrage de la lecture, les médias VOD sont débuts à 0 et les débuts de médias en direct au point d’accès client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.

1. Transmettez une position à `MediaPlayer.prepareToPlay`.

   TVSDK considère la position donnée comme le point de départ de la ressource et aucune opération de recherche n’est requise. Si la position n’est pas comprise dans la plage recherchée, TVSDK utilise la position par défaut. Pour plus d’informations, voir [Chargement d’une ressource média dans le lecteur de médias](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md).

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

