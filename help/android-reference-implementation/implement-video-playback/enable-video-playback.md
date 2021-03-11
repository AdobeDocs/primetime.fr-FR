---
description: Créez un PlaybackManager qui gère l’opération de configuration et de lecture du flux HLS. Aucune autre configuration n’est requise.
title: Activer la lecture vidéo
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Activer la lecture vidéo {#enable-video-playback}

Créez un PlaybackManager qui gère l’opération de configuration et de lecture du flux HLS. Aucune autre configuration n’est requise.

1. Créez l’objet du lecteur multimédia en vous assurant que le code suivant existe dans [!DNL PlayerFragment.java] :

   ```java
   private MediaPlayer createMediaPlayer() { 
           MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
           return mediaPlayer;
   ```

   <!-- I've duplicated this information. It also exists in the PlayerFragment section, just before the Feature manager section. I figured that I should have it here as well, in case they jump directly to this section.-->

1. Créez le gestionnaire de lecture à l’aide du `ManagerFactory` :

   ```java
   playbackManager = ManagerFactory.getPlaybackManager(config, mediaPlayer);
   ```

1. Mettez en oeuvre le `PlaybackManagerEventListener` dans le `PlayerFragment` pour gérer les événements de lecture :

   ```java
   private final PlaybackManagerEventListener playbackManagerEventListener =  
     new PlaybackManagerEventListener() 
   ```

1. Enregistrez l&#39;écouteur de événement dans le `PlayerFragment` :

   ```
   playbackManager.addEventListener(playbackManagerEventListener);
   ```

1. Configurez la ressource vidéo :

   ```
   playbackManager.setupVideo(url, adsManager); 
   ```

1. Configurez les opérations de la barre de contrôle dans le `PlayerFragment` :

   ```
   controlBar.pressPlay() { 
       playbackManager.play();  
   }
   ```

## Documentation de l&#39;API associée {#related-api-documentation}

* [Gestionnaire de lecture de classe](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.html)
* [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)
* [mediacore.utils.TimeRange](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/utils/TimeRange.html)
* [mediacore.BufferControlParameters](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/BufferControlParameters.html)
* [mediacore.MediaPlayer.PlayerState](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/MediaPlayer.PlayerState.html)