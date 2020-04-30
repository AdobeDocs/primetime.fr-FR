---
description: Lorsqu’un utilisateur clique sur une publicité, votre application doit interrompre la lecture du contenu vidéo principal.
seo-description: Lorsqu’un utilisateur clique sur une publicité, votre application doit interrompre la lecture du contenu vidéo principal.
seo-title: Pause et reprise de la lecture
title: Pause et reprise de la lecture
uuid: 87ba9f05-912d-4b85-8add-feb26a796a3a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

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

