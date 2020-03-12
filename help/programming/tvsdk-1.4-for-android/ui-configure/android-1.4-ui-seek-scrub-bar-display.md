---
description: TVSDK prend en charge la recherche d'une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, à la fois dans la vidéo à la demande (VOD) et les flux en direct.
seo-description: TVSDK prend en charge la recherche d'une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, à la fois dans la vidéo à la demande (VOD) et les flux en direct.
seo-title: Affichage d’une barre de défilement de recherche avec la position de lecture actuelle
title: Affichage d’une barre de défilement de recherche avec la position de lecture actuelle
uuid: a9f4dd6c-78cf-455c-8c31-b2f7b740d84a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Affichage d’une barre de défilement de recherche avec la position de lecture actuelle {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK prend en charge la recherche d&#39;une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, à la fois dans la vidéo à la demande (VOD) et les flux en direct.

>[!IMPORTANT]
>
>La recherche dans un flux en direct n’est autorisée que pour le DVR.

1. Configurez les rappels pour la recherche.

       La recherche étant asynchrone, TVSDK distribue les  de recherche suivantes :
   
   * `QOSEventListener.onSeekStart` - Cherche à démarrer.
   * `QOSEventListener.onSeekComplete` - Recherche réussie.
   * `QOSEventListener.onOperationFailed` - Échec de la recherche.

1. Attendez que le lecteur soit dans un état valide pour la recherche.

   Les états valides sont PREPARRED, COMPLETE, PAUSED et PLAYING.

1. Utilisez la barre de recherche native pour définir `OnSeekBarChangeListener` le moment où l’utilisateur fait défiler l’écran.
1. Écoutez `QOSEventListener.onOperationFailed` et prenez les mesures appropriées.

   Ce transmet l’avertissement approprié. Votre application détermine comment procéder, par exemple, en tentant à nouveau la recherche ou en continuant la lecture à partir de la position précédente.

1. Attendez que TVSDK appelle le `QOSEventListener.onSeekComplete` rappel.
1. Récupérez la position de lecture modifiée finale à l’aide du paramètre position du rappel.

   C’est important car la position réelle du après la recherche peut être différente de la position demandée. Le comportement de lecture peut être affecté si une recherche ou un autre repositionnement se termine au milieu d’une coupure publicitaire ou saute des pauses publicitaires.

1. Utilisez les informations de position lors de l’affichage d’une barre de défilement de recherche.

<!--<a id="example_9657AA855B6A4355B0E7D854596FFB54"></a>-->

**Exemple de recherche**

Dans cet exemple, l’utilisateur fait défiler la barre de recherche pour rechercher la position souhaitée.

```java
// Use the native SeekBar to set OnSeekBarChangeListener to  
//see when the user is scrubbing. 
seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() { 
 
    @Override 
    public void onProgressChanged(SeekBar seekBar, int progress, boolean isFromUser) { 
        if (isFromUser) {  
            // Update the seek bar thumb, with the position provided by the user. 
            setPosition(progress); 
        } 
    } 
 
    @Override 
    public void onStartTrackingTouch(SeekBar seekBar) { 
        isSeeking = true; 
    } 
 
    @Override 
    public void onStopTrackingTouch(SeekBar seekBar) { 
        isSeeking = false; 
        // Retrieve the playback range. 
        TimeRange playbackRange = mediaPlayer.getPlaybackRange(); 
        // Make sure to seek inside the playback range. 
        long seekPosition = Math.min(Math.round(seekBar.getProgress()),  
                                     playbackRange.getDuration()); 
        // Perform seek. 
        seek(playbackRange.getBegin() + seekPosition); 
    } 
}; 
```

