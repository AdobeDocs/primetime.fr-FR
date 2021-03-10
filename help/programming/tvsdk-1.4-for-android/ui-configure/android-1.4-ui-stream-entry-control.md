---
description: Par défaut, lors du démarrage de la lecture, le média VOD début à 0 (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
title: Entrer un flux à un moment donné
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 2%

---


# Entrer un flux à un moment spécifique {#enter-a-stream-at-a-specific-time}

Par défaut, lors du démarrage de la lecture, le média VOD début à 0 (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.

1. Transmettez une position à `MediaPlayer.prepareToPlay`.

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

