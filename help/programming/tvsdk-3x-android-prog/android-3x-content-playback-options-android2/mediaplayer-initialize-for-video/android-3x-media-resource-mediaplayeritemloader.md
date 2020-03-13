---
description: L’utilisation de MediaPlayerItemLoader permet d’obtenir des informations sur un flux média sans instancier une instance MediaPlayer. Ceci est particulièrement utile dans les flux de pré-mise en mémoire tampon afin que la lecture puisse commencer sans délai.
seo-description: L’utilisation de MediaPlayerItemLoader permet d’obtenir des informations sur un flux média sans instancier une instance MediaPlayer. Ceci est particulièrement utile dans les flux de pré-mise en mémoire tampon afin que la lecture puisse commencer sans délai.
seo-title: Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader
title: Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader
uuid: 504063af-1dd4-4268-88e7-ad5a247fdff7
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

L’utilisation de MediaPlayerItemLoader permet d’obtenir des informations sur un flux média sans instancier une instance MediaPlayer. Ceci est particulièrement utile dans les flux de pré-mise en mémoire tampon afin que la lecture puisse commencer sans délai.

La `MediaPlayerItemLoader` classe vous permet d’échanger une ressource multimédia pour la ressource `MediaPlayerItem` actuelle sans associer un à une `MediaPlayer` instance, ce qui affecterait des ressources matérielles de décodage vidéo. Des étapes supplémentaires sont nécessaires pour le contenu protégé par DRM, mais ce guide ne les décrit pas.

>[!IMPORTANT]
>
>TVSDK ne prend pas en charge un seul `QoSProvider` pour travailler avec `itemLoader` et `MediaPlayer`. Si votre application utilise Instant On, elle doit gérer deux `QoS` instances et les deux instances pour les informations. Voir [Instant-on](../../android-3x-content-playback-options-android2/buffering-configuration/android-3x-instant-on.md) pour plus d’informations.

1. Créez une instance de `MediaPlayerItemLoader`.

   ```java
   private MediaPlayerItemLoader createLoader() { 
       MediaPlayerItemLoader itemLoader =   
         new MediaPlayerItemLoader(this, new MediaPlayerItemLoader.LoaderListener() { 
           public void onError(PSDKErrorCode mediaErrorCode, String description) { 
               //Do something 
           } 
   
           public void onLoadComplete(MediaPlayerItem playerItem) { 
               loader.prepareBuffer(); 
           } 
   
           public void onBufferingBegin() { 
               //Do something 
           } 
   
           public void onBufferPrepared() { 
               mPlayer.reset(); 
           }  
       }); 
   
       itemLoader.setKeepRebufferingForLive(true); 
       return itemLoader; 
   } 
   ```

   >[!TIP]
   >
   >Créez une instance distincte de `MediaPlayerItemLoader` pour chaque ressource. N’utilisez pas une seule `MediaPlayerItemLoader` instance pour charger plusieurs ressources.

1. Implémentez la `ItemLoaderListener` classe pour recevoir des notifications de l’ `MediaPlayerItemLoader` instance.

   ```java
   private MediaPlayerItemLoader createLoader() { 
       MediaPlayerItemLoader itemLoader =   
         new MediaPlayerItemLoader(this, new MediaPlayerItemLoader.LoaderListener() { 
           public void onError(PSDKErrorCode mediaErrorCode, String description) { 
               //Do something 
           } 
           public void onLoadComplete(MediaPlayerItem playerItem) { 
               loader.prepareBuffer(); 
           } 
           public void onBufferingBegin() { 
               //Do something 
           } 
           public void onBufferPrepared() { 
               mPlayer.reset(); 
           }  
       } ); 
   
       itemLoader.setKeepRebufferingForLive(true); 
       return itemLoader; 
   }
   ```

   Dans le `onLoadComplete()` rappel, effectuez l’une des opérations suivantes :

   * Assurez-vous que tout élément susceptible d’affecter la mise en mémoire tampon, par exemple, la sélection de pistes WebVTT ou audio, est complet et appelez `prepareBuffer()` pour tirer parti de l’instant présent.
   * Joignez l’élément à l’ `MediaPlayer` instance à l’aide de `replaceCurrentItem()`.
   Si vous appelez `prepareBuffer()`, vous recevez le BUFFER_PREPARED dans votre `onBufferPrepared` gestionnaire une fois la préparation terminée.
1. Appelez `load` l’ `MediaPlayerItemLoader` instance et transmettez la ressource à charger, ainsi que éventuellement l’ID de contenu et une `MediaPlayerItemConfig` instance.

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. Pour mettre en mémoire tampon à partir d’un point autre que le début du flux, appelez `prepareBuffer()` avec la position (en millisecondes) à laquelle vous souhaitez la mise en mémoire tampon.
1. Utilisez les `replaceCurrentItem()` méthodes et `play()` les méthodes de `MediaPlayer` manière à la lecture à partir de ce point.
1. Attendez l&#39;état inactif et appelez `replaceCurrentItem`.
1. Lecture de l’élément.

   * Si l’élément est chargé mais pas mis en mémoire tampon :

      1. Attendez l’état initialisé.
      1. Appelle `prepareToPlay()`.
      1. Attendez l’état PRÉPARÉ.
      1. Appelle `play()`.
   * Si l’élément est mis en mémoire tampon :

      1. Attendez le préparé par la mémoire tampon.
      1. Appelle `play()`.