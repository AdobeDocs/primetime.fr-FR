---
seo-title: Activer l’audio en arrière-plan
title: Activer l’audio en arrière-plan
uuid: aa6dc934-e85c-4db1-901b-9777f47106e6
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# Activer l&#39;audio en arrière-plan {#enable-background-audio}

Pour activer la lecture audio lorsque l’application est en arrière-plan, l’application doit appeler l’API `enableAudioPlaybackInBackground` de MediaPlayer avec la valeur true en tant qu’argument lorsque le lecteur est à l’état PRÉPARÉ.

```
_mediaPlayer.enableAudioPlaybackInBackground(true);
```

L’application doit interrompre la lecture lorsqu’elle perd son contrôle sur la mise au point audio pendant les événements, par exemple en répondant au téléphone, etc. Le fragment de code suivant montre comment implémenter `OnAudioFocusChangeListener` :

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
