---
description: Par défaut, lors du démarrage de la lecture, les médias VOD sont débuts à 0 et les débuts de médias en direct au point d’accès client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
seo-description: Par défaut, lors du démarrage de la lecture, les médias VOD sont débuts à 0 et les débuts de médias en direct au point d’accès client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
seo-title: Entrer un flux à un moment donné
title: Entrer un flux à un moment donné
uuid: 65a19192-b890-4d69-9cb1-582a22988d2b
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184
workflow-type: tm+mt
source-wordcount: '150'
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

