---
description: TVSDK prend en charge la recherche vers une position spécifique (heure) où la diffusion est une liste de lecture de fenêtre glissante, à la fois dans la vidéo à la demande (VOD) et dans les diffusions en direct.
title: Afficher une barre de défilement de recherche avec la position de lecture actuelle
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Afficher une barre de défilement de recherche avec la position de lecture actuelle {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK prend en charge la recherche vers une position spécifique (heure) où la diffusion est une liste de lecture de fenêtre glissante, à la fois dans la vidéo à la demande (VOD) et dans les diffusions en direct.

>[!IMPORTANT]
>
>La recherche dans une diffusion en direct n’est autorisée que pour les enregistrements DVR.

1. Configurez les rappels pour la recherche.

       La recherche étant asynchrone, TVSDK distribue les événements liés à la recherche suivants :
   
   * `QOSEventListener.onSeekStart` - Recherche en cours.
   * `QOSEventListener.onSeekComplete` - Recherche réussie.
   * `QOSEventListener.onOperationFailed` - Échec de la recherche.

1. Attendez que le lecteur soit dans un état valide pour la recherche.

   Les états valides sont PRÉPARÉS, TERMINÉS, EN PAUSE et EN LECTURE.

1. Utilisez la barre de recherche native pour définir `OnSeekBarChangeListener` pour voir quand l’utilisateur effectue un défilement.
1. Listen for `QOSEventListener.onOperationFailed` et prendre les mesures appropriées.

   Cet événement transmet l’avertissement approprié. Votre application détermine comment procéder, par exemple, en essayant de relancer la recherche ou en continuant la lecture à partir de la position précédente.

1. Attendez que TVSDK appelle la fonction `QOSEventListener.onSeekComplete` rappel.
1. Récupérez la position de lecture ajustée finale à l’aide du paramètre position du rappel.

   Ceci est important, car la position de départ réelle après la recherche peut être différente de celle requise. Le comportement de lecture peut être affecté si une recherche ou un autre repositionnement se termine au milieu d’une coupure publicitaire ou ignore les coupures publicitaires.

1. Utilisez les informations de position lors de l’affichage d’une barre de défilement de recherche.

<!--<a id="example_9657AA855B6A4355B0E7D854596FFB54"></a>-->

**Exemple de recherche**

Dans cet exemple, l’utilisateur fait défiler la barre de recherche pour accéder à la position souhaitée.

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
