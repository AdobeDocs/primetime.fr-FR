---
description: TVSDK prend en charge la recherche d'une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, dans la vidéo à la demande (VOD) et les flux en direct.
seo-description: TVSDK prend en charge la recherche d'une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, dans la vidéo à la demande (VOD) et les flux en direct.
seo-title: Affichage d’une barre de défilement de recherche avec la position de lecture actuelle
title: Affichage d’une barre de défilement de recherche avec la position de lecture actuelle
uuid: df045a10-8d74-4874-8fa5-7e9571c8678d
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Affichage d’une barre de défilement de recherche avec la position de lecture actuelle {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK prend en charge la recherche d&#39;une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, dans la vidéo à la demande (VOD) et les flux en direct.

>[!TIP]
>
>La recherche dans un flux en direct n’est autorisée que pour le DVR.

1. Configurez les rappels pour la recherche.

       La recherche étant asynchrone, TVSDK distribue les  de recherche suivantes :
   
   * `MediaPlayerEvent.SEEK_BEGIN`, où le de recherche .
   * `MediaPlayerEvent.SEEK_END`, où la recherche réussit.
   * `MediaPlayerEvent.OPERATION_FAILED`, où la recherche a échoué.

1. Attendez que le lecteur soit dans un état valide pour la recherche.

   Les états valides sont PRÉPARÉS, TERMINÉS, EN PAUSE et EN COURS DE LECTURE.
1. Utilisez le paramètre natif `SeekBar` à définir `OnSeekBarChangeListener`, qui détermine le moment où l’utilisateur effectue un défilement.
1. Transmettez la position de recherche demandée (millisecondes) à la `MediaPlayer.seek` méthode.

   ```java
   void seek(long position) throws MediaPlayerException;
   ```

   Vous pouvez effectuer une recherche uniquement dans la durée recherchée de la ressource. Pour la vidéo à la demande, c’est-à-dire de 0 à la durée de la ressource.

   >[!TIP]
   >
   >Cette étape déplace la tête de lecture vers une nouvelle position dans le flux, mais la position calculée finale peut différer de la position de recherche spécifiée.

1. Écoutez `MediaPlayerEvent.OPERATION_FAILED` et prenez les mesures appropriées.

   Ce transmet l’avertissement approprié. Votre application détermine comment procéder et les options incluent de relancer la recherche ou de poursuivre la lecture à partir de la position précédente.

1. Attendez que TVSDK appelle le `MediaPlayerEvent.SEEK_END` rappel.
1. Récupérez la position de lecture modifiée finale à l’aide du paramètre position du rappel.

   C’est important car la position réelle du après la recherche peut être différente de la position demandée. Des règles, y compris le comportement de lecture, sont affectées si une recherche ou un autre repositionnement se termine au milieu d’une coupure publicitaire ou saute des pauses publicitaires, peuvent s’appliquer.

1. Utilisez les informations de position lors de l’affichage d’une barre de défilement de recherche.

<!--<a id="example_EEB73818260C43C8B5AE12BA68548AB7"></a>-->

**Exemple de recherche**

Dans cet exemple, l’utilisateur fait défiler la barre de recherche pour rechercher la position souhaitée.

```java
//Use the native SeekBar to set an OnSeekBarChangeListener to 
// see when the user is scrubbing. 
seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() { 
    @Override 
    public void onProgressChanged(SeekBar seekBar, int progress, boolean isFromUser) { 
        if (isFromUser) { 
            // Update the seek bar thumb with the position provided by the user. 
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

