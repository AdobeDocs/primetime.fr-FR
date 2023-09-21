---
description: TVSDK prend en charge la recherche vers une position spécifique (temps) où la diffusion est une liste de lecture de fenêtre glissante, dans la vidéo à la demande (VOD) et les diffusions en direct.
title: Afficher une barre de défilement de recherche avec la position de lecture actuelle
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Afficher une barre de défilement de recherche avec la position de lecture actuelle {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK prend en charge la recherche vers une position spécifique (temps) où la diffusion est une liste de lecture de fenêtre glissante, dans la vidéo à la demande (VOD) et les diffusions en direct.

>[!TIP]
>
>La recherche dans une diffusion en direct n’est autorisée que pour les enregistrements DVR.

1. Configurez les rappels pour la recherche.

       La recherche étant asynchrone, TVSDK distribue les événements liés à la recherche suivants :
   
   * `MediaPlayerEvent.SEEK_BEGIN`, où la recherche commence.
   * `MediaPlayerEvent.SEEK_END`, où la recherche a réussi.
   * `MediaPlayerEvent.OPERATION_FAILED`, où la recherche a échoué.

1. Attendez que le lecteur soit dans un état valide pour la recherche.

   Les états valides sont PRÉPARÉS, TERMINÉS, EN PAUSE et EN LECTURE.
1. Utilisez le paramètre natif `SeekBar` à définir `OnSeekBarChangeListener`, qui détermine le moment où l’utilisateur effectue un défilement.
1. Transmettez la position de recherche demandée (en millisecondes) à la variable `MediaPlayer.seek` .

   ```java
   void seek(long position) throws MediaPlayerException;
   ```

   Vous ne pouvez effectuer des recherches que dans la durée de recherche de la ressource. Pour une vidéo à la demande, c’est-à-dire de 0 à la durée de la ressource.

   >[!TIP]
   >
   >Cette étape déplace la tête de lecture vers une nouvelle position dans le flux, mais la position finale calculée peut différer de la position de recherche spécifiée.

1. Listen for `MediaPlayerEvent.OPERATION_FAILED` et prendre les mesures appropriées.

   Cet événement transmet l’avertissement approprié. Votre application détermine comment procéder et les options incluent la reprise de la recherche ou la poursuite de la lecture à partir de la position précédente.

1. Attendez que TVSDK appelle la fonction `MediaPlayerEvent.SEEK_END` rappel.
1. Récupérez la position de lecture ajustée finale à l’aide du paramètre position du rappel.

   Ceci est important, car la position de départ réelle après la recherche peut être différente de celle requise. Des règles, y compris le comportement de lecture, sont affectées si une recherche ou un autre repositionnement se termine au milieu d’une coupure publicitaire ou si elle ignore les coupures publicitaires, peuvent s’appliquer.

1. Utilisez les informations de position lors de l’affichage d’une barre de défilement de recherche.

<!--<a id="example_EEB73818260C43C8B5AE12BA68548AB7"></a>-->

**Exemple de recherche**

Dans cet exemple, l’utilisateur fait défiler la barre de recherche pour accéder à la position souhaitée.

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
