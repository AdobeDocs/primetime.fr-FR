---
description: L’utilisation de MediaPlayerItemLoader permet d’obtenir des informations sur un flux média sans instancier une instance MediaPlayer. Cela s’avère particulièrement utile dans les flux de mise en mémoire tampon afin que la lecture puisse commencer sans délai.
seo-description: L’utilisation de MediaPlayerItemLoader permet d’obtenir des informations sur un flux média sans instancier une instance MediaPlayer. Cela s’avère particulièrement utile dans les flux de mise en mémoire tampon afin que la lecture puisse commencer sans délai.
seo-title: Chargement d'une ressource multimédia à l'aide de MediaPlayerItemLoader
title: Chargement d'une ressource multimédia à l'aide de MediaPlayerItemLoader
uuid: 504063af-1dd4-4268-88e7-ad5a247fdff7
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# Chargement d&#39;une ressource multimédia à l&#39;aide de MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

L’utilisation de MediaPlayerItemLoader permet d’obtenir des informations sur un flux média sans instancier une instance MediaPlayer. Cela s’avère particulièrement utile dans les flux de mise en mémoire tampon afin que la lecture puisse commencer sans délai.

La `MediaPlayerItemLoader` classe vous permet d&#39;échanger une ressource multimédia pour le contenu actuel `MediaPlayerItem` sans attacher une vue à une `MediaPlayer` instance, ce qui affecterait des ressources matérielles de décodage vidéo. Des étapes supplémentaires sont nécessaires pour le contenu protégé par DRM, mais ce manuel ne les décrit pas.

>[!IMPORTANT]
>
>TVSDK ne prend pas en charge un seul `QoSProvider` pour travailler à la fois `itemLoader` et `MediaPlayer`. Si votre application utilise Instant On, elle doit gérer deux `QoS` instances et gérer les deux instances pour les informations. Voir [Instant](../../android-3x-content-playback-options-android2/buffering-configuration/android-3x-instant-on.md) pour plus d’informations.

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

1. Implémentez la `ItemLoaderListener` classe pour recevoir des notifications de l&#39; `MediaPlayerItemLoader` instance.

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

   * Assurez-vous que tout ce qui peut avoir une incidence sur la mise en mémoire tampon, par exemple, la sélection de pistes WebVTT ou audio, est terminé et appelez `prepareBuffer()` pour profiter de l&#39;instant présent.
   * Joignez l’élément à l’ `MediaPlayer` instance en utilisant `replaceCurrentItem()`.
   Si vous appelez `prepareBuffer()`, vous recevez le événement BUFFER_PREPARED dans votre `onBufferPrepared` gestionnaire une fois la préparation terminée.
1. Appelez `load` l’ `MediaPlayerItemLoader` instance et transmettez la ressource à charger, et éventuellement l’ID de contenu, ainsi qu’une `MediaPlayerItemConfig` instance.

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. Pour mettre en mémoire tampon depuis un point autre que le début du flux, appelez `prepareBuffer()` avec la position (en millisecondes) à laquelle la mise en mémoire tampon début.
1. Utilisez les `replaceCurrentItem()` et `play()` méthodes de `MediaPlayer` début de la lecture à partir de ce point.
1. Attendez l&#39;état inactif et appelez `replaceCurrentItem`.
1. Lire l’élément.

   * Si l&#39;élément est chargé mais pas mis en mémoire tampon :

      1. Attendez l’état initialisé.
      1. Appelle `prepareToPlay()`.
      1. Attendez l’état PRÉPARÉ.
      1. Appelle `play()`.
   * Si l&#39;élément est mis en mémoire tampon :

      1. Attendez le événement préparé pour la mémoire tampon.
      1. Appelle `play()`.