---
title: Activation du son en arrière-plan
description: Activation du son en arrière-plan
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---

# Activation du son en arrière-plan {#enable-background-audio}

Pour activer la lecture audio lorsque l’application est en arrière-plan, l’application doit appeler `enableAudioPlaybackInBackground` API de MediaPlayer avec la valeur true en tant qu’argument lorsque le lecteur est à l’état PRÉPARÉ.

```
_mediaPlayer.enableAudioPlaybackInBackground(true);
```

L’application doit suspendre la lecture lorsqu’elle perd son contrôle sur la mise au point audio lors d’événements tels que la réponse au téléphone, etc. Le fragment de code suivant montre comment mettre en oeuvre le `OnAudioFocusChangeListener`:

```
/** 
 * Register the AudioFocus Change listener to track Audio focus from device. 
 */ 
 AudioManager.OnAudioFocusChangeListener onAudioFocusChangeListener = new AudioManager.OnAudioFocusChangeListener(){ 
     @Override 
     public void onAudioFocusChange(int focusChange){ 
          switch(focusChange){ 
               case AudioManager.AUDIOFOCUS_GAIN: 
                    break; 
               case AudioManager.AUDIOFOCUS_LOSS_TRANSIENT_CAN_DUCK: 
                    /* lower output volume*/ 
                    break; 
               case AudioManager.AUDIOFOCUS_LOSS: 
               case AudioManager.AUDIOFOCUS_LOSS_TRANSIENT: 
                    if(_lastKnownStatus ==MediaPlayerStatus.PLAYING) 
                         _mediaPlayer.pause(); 
                    break; 
          } 
     } 
}; 
 
AudioManager audioManager = (AudioManager) getActivity().getApplicationContext().getSystemService(Context.AUDIO_SERVICE); 
audioManager.requestAudioFocus(onAudioFocusChangeListener, AudioManager.STREAM_MUSIC, AudioManager.AUDIOFOCUS_GAIN);
```
