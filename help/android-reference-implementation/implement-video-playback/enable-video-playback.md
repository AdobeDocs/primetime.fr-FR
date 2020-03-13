---
description: Créez un PlaybackManager qui gère la configuration du flux HLS et l’opération de lecture. Aucune autre configuration n’est requise.
seo-description: Créez un PlaybackManager qui gère la configuration du flux HLS et l’opération de lecture. Aucune autre configuration n’est requise.
seo-title: Activer la lecture vidéo
title: Activer la lecture vidéo
uuid: ddc0defa-c40f-4ee6-a69f-d5eeca6c2fce
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d

---


# Activer la lecture vidéo {#enable-video-playback}

Créez un PlaybackManager qui gère la configuration du flux HLS et l’opération de lecture. Aucune autre configuration n’est requise.

1. Créez l’objet du lecteur multimédia en vous assurant que le code suivant existe dans [!DNL PlayerFragment.java]:

   ```java
   private MediaPlayer createMediaPlayer() { 
           MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
           return mediaPlayer;
   ```

   <!-- I've duplicated this information. It also exists in the PlayerFragment section, just before the Feature manager section. I figured that I should have it here as well, in case they jump directly to this section.-->

1. Créez le gestionnaire de lecture via `ManagerFactory`:

   ```java
   playbackManager = ManagerFactory.getPlaybackManager(config, mediaPlayer);
   ```

1. Mettez en oeuvre le `PlaybackManagerEventListener` dans `PlayerFragment` pour gérer le de lecture :

   ```java
   private final PlaybackManagerEventListener playbackManagerEventListener =  
     new PlaybackManagerEventListener() 
   ```

1. Enregistrez l’écouteur de  dans `PlayerFragment`:

   ```
   playbackManager.addEventListener(playbackManagerEventListener);
   ```

1. Configurez la ressource vidéo :

   ```
   playbackManager.setupVideo(url, adsManager); 
   ```

1. Configurez les opérations de la barre de contrôle dans `PlayerFragment`:

   ```
   controlBar.pressPlay() { 
       playbackManager.play();  
   }
   ```

## Documentation sur les API connexes {#related-api-documentation}

* [Classe PlaybackManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.html)
* [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)
* [mediacore.utils.TimeRange](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/utils/TimeRange.html)
* [mediacore.BufferControlParameters](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/BufferControlParameters.html)
* [mediacore.MediaPlayer.PlayerState](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/MediaPlayer.PlayerState.html)