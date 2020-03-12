---
description: Lorsqu’un utilisateur clique sur une publicité, votre application doit interrompre la lecture du contenu vidéo principal.
seo-description: Lorsqu’un utilisateur clique sur une publicité, votre application doit interrompre la lecture du contenu vidéo principal.
seo-title: Suspendre et reprendre la lecture
title: Suspendre et reprendre la lecture
uuid: a8fec392-3a71-4086-abf1-23522d023680
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Suspendre et reprendre la lecture {#pause-and-resume-playback}

Lorsqu’un utilisateur clique sur une publicité, votre application doit interrompre la lecture du contenu vidéo principal.

Remplacez le `onPause` et `onResume` du  de  Android.

```java
@Override 
public void onResume() { 
    super.onResume(); 
    requestAudioFocus(); 
    if (_lastKnownStatus == MediaPlayer.PlayerState.PAUSED) { 
        _mediaPlayer.play(); 
    } 
} 
... 
 
@Override 
public void onPause() { 
    super.onPause(); 
    if (_mediaPlayer != null) { 
        if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PLAYING || 
          _mediaPlayer.getStatus() == MediaPlayer.PlayerState.PAUSED) { 
            _savedPlayerState = _mediaPlayer.getStatus(); 
            _lastKnownTime = _mediaPlayer.getCurrentTime(); 
        } 
        if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PLAYING) { 
            _mediaPlayer.pause(); 
            _lastKnownStatus = MediaPlayer.PlayerState.PAUSED; 
        } 
    } 
} 
 
abandonAudioFocus(); 
```

