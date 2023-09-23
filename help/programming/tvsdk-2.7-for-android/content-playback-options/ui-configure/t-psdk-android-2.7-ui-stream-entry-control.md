---
description: Par défaut, lors du démarrage de la lecture, le média VOD démarre à 0 et le média en direct démarre au point d’exécution client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
title: Saisie d’un flux à un moment spécifique
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Saisie d’un flux à un moment spécifique {#enter-a-stream-at-a-specific-time}

Par défaut, lors du démarrage de la lecture, le média VOD démarre à 0 et le média en direct démarre au point d’exécution client (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.

1. Transmettre une position à `MediaPlayer.prepareToPlay`.

   TVSDK considère la position donnée comme le point de départ de la ressource et aucune opération de recherche n’est requise. Si la position ne se trouve pas dans la plage pouvant faire l’objet d’une recherche, TVSDK utilise la position par défaut. Pour plus d’informations, voir [Chargement d’une ressource multimédia dans le lecteur multimédia](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md).

   Par exemple :

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
