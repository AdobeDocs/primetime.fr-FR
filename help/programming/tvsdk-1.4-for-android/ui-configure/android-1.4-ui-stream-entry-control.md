---
description: Par défaut, au démarrage de la lecture, le média VOD démarre à 0 (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.
title: Saisie d’un flux à un moment spécifique
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Saisie d’un flux à un moment spécifique {#enter-a-stream-at-a-specific-time}

Par défaut, au démarrage de la lecture, le média VOD démarre à 0 (MediaPlayer.LIVE_POINT). Vous pouvez remplacer le comportement par défaut.

1. Transmettre une position à `MediaPlayer.prepareToPlay`.

   TVSDK considère la position donnée comme le point de départ de la ressource. Aucune opération de recherche n’est requise. Si la position ne se trouve pas dans la plage pouvant faire l’objet d’une recherche, TVSDK utilise la position par défaut.

   Par exemple :

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
