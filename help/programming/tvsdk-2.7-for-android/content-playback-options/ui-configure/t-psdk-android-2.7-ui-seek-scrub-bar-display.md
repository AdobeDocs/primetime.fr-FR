---
description: TVSDK prend en charge la recherche à une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, dans la vidéo à la demande (VOD) et les flux en direct.
seo-description: TVSDK prend en charge la recherche à une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, dans la vidéo à la demande (VOD) et les flux en direct.
seo-title: Affichage d’une barre de défilement de recherche avec la position de lecture actuelle
title: Affichage d’une barre de défilement de recherche avec la position de lecture actuelle
uuid: df045a10-8d74-4874-8fa5-7e9571c8678d
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Affichage d’une barre de défilement de recherche avec la position de lecture actuelle {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK prend en charge la recherche à une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, dans la vidéo à la demande (VOD) et les flux en direct.

>[!TIP]
>
>La recherche dans un flux en direct n&#39;est autorisée que pour le magnétoscope numérique.

1. Configurez les rappels pour la recherche.

       La recherche étant asynchrone, TVSDK distribue les événements suivants liés à la recherche :
   
   * `MediaPlayerEvent.SEEK_BEGIN`, où les débuts de recherche.
   * `MediaPlayerEvent.SEEK_END`, où la recherche a réussi.
   * `MediaPlayerEvent.OPERATION_FAILED`, où la recherche a échoué.

1. Attendez que le lecteur ait un état valide pour la recherche.

   Les états valides sont PRÉPARÉS, TERMINÉS, PAUSED et PLAYING.
1. Utilisez l’élément natif `SeekBar` pour définir `OnSeekBarChangeListener`, qui détermine le moment où l’utilisateur fait défiler les données.
1. Transmettez la position de recherche demandée (millisecondes) à la méthode `MediaPlayer.seek`.

   ```java
   void seek(long position) throws MediaPlayerException;
   ```

   Vous ne pouvez effectuer des recherches que dans la durée recherchée de la ressource. Pour la vidéo à la demande, il s’agit de 0 jusqu’à la durée de la ressource.

   >[!TIP]
   >
   >Cette étape déplace la tête de lecture vers une nouvelle position dans le flux, mais la position finale calculée peut différer de la position de recherche spécifiée.

1. Prêtez attention à `MediaPlayerEvent.OPERATION_FAILED` et prenez les mesures appropriées.

   Ce événement transmet l&#39;avertissement approprié. Votre application détermine comment procéder et les options incluent la tentative de nouvelle recherche ou la poursuite de la lecture à partir de la position précédente.

1. Attendez que TVSDK appelle le rappel `MediaPlayerEvent.SEEK_END`.
1. Récupérez la position de lecture modifiée finale à l’aide du paramètre de position du rappel.

   Ceci est important car la position réelle du début après la recherche peut être différente de la position demandée. Des règles, y compris le comportement de lecture, sont affectées si une recherche ou un autre repositionnement se termine au milieu d’une coupure publicitaire ou saute des pauses publicitaires, peuvent s’appliquer.

1. Utilisez les informations de position lors de l&#39;affichage d&#39;une barre de défilement de recherche.

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

