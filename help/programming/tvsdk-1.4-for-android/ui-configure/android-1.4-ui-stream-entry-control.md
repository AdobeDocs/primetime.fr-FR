---
description: Par défaut, lors du démarrage de la lecture, le média VOD début à 0 (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
seo-description: Par défaut, lors du démarrage de la lecture, le média VOD début à 0 (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
seo-title: Entrer un flux à un moment donné
title: Entrer un flux à un moment donné
uuid: ac3479e2-46a1-4ac8-a9e8-68a23f5dd74d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Entrer un flux à un moment donné {#enter-a-stream-at-a-specific-time}

Par défaut, lors du démarrage de la lecture, le média VOD début à 0 (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.

1. Passez une position à `MediaPlayer.prepareToPlay`.

   TVSDK considère la position donnée comme le point de départ de la ressource. Aucune opération de recherche n&#39;est requise. Si la position n’est pas comprise dans la plage recherchée, TVSDK utilise la position par défaut.

   Par exemple :

   ```java
   long desiredPostion = //TODO : choose a value; 
   @Override 
   public void onStateChanged(MediaPlayer.PlayerState state, MediaPlayerNotification notification) { 
       switch (state) { 
           case INITIALIZED: 
               _mediaPlayer.prepareToPlay(desiredPosition); 
               break; 
               case PREPARING: 
               showBufferingSpinner(); 
               break; 
           ... 
       } 
   } 
   ```

