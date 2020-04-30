---
description: Lorsqu’un utilisateur clique sur une publicité, votre application doit interrompre la lecture du contenu vidéo principal.
seo-description: Lorsqu’un utilisateur clique sur une publicité, votre application doit interrompre la lecture du contenu vidéo principal.
seo-title: Pause et reprise de la lecture
title: Pause et reprise de la lecture
uuid: 229e2499-e30e-458c-bd6d-d035588c21cf
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Pause et reprise de la lecture {#pause-and-resume-playback}

Lorsqu’un utilisateur clique sur une publicité, votre application doit interrompre la lecture du contenu vidéo principal.

1. Remplacez l’Activité `onPause` et `onResume` depuis Android.

   ```java
   @Override 
   public void onResume() { 
       super.onResume(); 
       requestAudioFocus(); 
       if (_lastKnownStatus == MediaPlayerStatus.PAUSED) { 
           _mediaPlayer.play(); 
       } 
   } 
   ... 
   
   @Override 
   public void onPause() { 
       super.onPause(); 
       if (_mediaPlayer != null) { 
           if (_mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING || 
             _mediaPlayer.getStatus() == MediaPlayerStatus.PAUSED) { 
               _savedPlayerStatus = _mediaPlayer.getStatus(); 
               _lastKnownTime = _mediaPlayer.getCurrentTime(); 
           } 
           if (_mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING) { 
               _mediaPlayer.pause(); 
               _lastKnownStatus = MediaPlayerStatus.PAUSED; 
           } 
       } 
   } 
   abandonAudioFocus(); 
   ```

