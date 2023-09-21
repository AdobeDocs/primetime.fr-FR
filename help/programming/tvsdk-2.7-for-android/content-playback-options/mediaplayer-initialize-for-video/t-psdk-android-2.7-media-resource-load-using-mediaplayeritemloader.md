---
description: L’utilisation de MediaPlayerItemLoader vous permet d’obtenir des informations sur un flux multimédia sans instancier une instance MediaPlayer. Cela s’avère particulièrement utile dans les flux de pré-mise en mémoire tampon afin que la lecture puisse commencer sans délai.
title: Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

L’utilisation de MediaPlayerItemLoader vous permet d’obtenir des informations sur un flux multimédia sans instancier une instance MediaPlayer. Cela s’avère particulièrement utile dans les flux de pré-mise en mémoire tampon afin que la lecture puisse commencer sans délai.

La variable `MediaPlayerItemLoader` vous aide à échanger une ressource multimédia pour la classe actuelle ; `MediaPlayerItem` sans associer une vue à une `MediaPlayer` qui allouerait les ressources matérielles de décodage vidéo. Des étapes supplémentaires sont nécessaires pour le contenu protégé par DRM, mais ce manuel ne les décrit pas.

>[!IMPORTANT]
>
>TVSDK ne prend pas en charge une seule `QoSProvider` pour travailler avec les deux `itemLoader` et `MediaPlayer`. Si votre application utilise Instant On, l’application doit gérer deux `QoS` et gérez les deux instances pour les informations. Voir  [instantané](../../content-playback-options/buffering-configuration/c-psdk-android-2.7-instant-on.md) pour plus d’informations.

1. Création d’une instance de `MediaPlayerItemLoader`.

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
   >Création d’une instance distincte de `MediaPlayerItemLoader` pour chaque ressource. N’en utilisez pas un `MediaPlayerItemLoader` pour charger plusieurs ressources.

1. Mettez en oeuvre le `ItemLoaderListener` pour recevoir des notifications de la `MediaPlayerItemLoader` instance.

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

   Dans le `onLoadComplete()` effectuez l’une des opérations suivantes :

   * Assurez-vous que tout élément susceptible d’affecter la mise en mémoire tampon, par exemple la sélection de pistes WebVTT ou audio, est terminé et appelez `prepareBuffer()` pour profiter de l&#39;instant présent.
   * Joindre l’élément au `MediaPlayer` en utilisant `replaceCurrentItem()`.

   Si vous appelez `prepareBuffer()`, vous recevez l’événement BUFFER_PREPARED dans votre `onBufferPrepared` gestionnaire une fois la préparation terminée.

1. Appeler `load` sur le `MediaPlayerItemLoader` et transmettez la ressource à charger, et éventuellement l’identifiant de contenu, et un `MediaPlayerItemConfig` instance.

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. Pour mettre en mémoire tampon à partir d’un point autre que le début de la diffusion, appelez `prepareBuffer()` avec la position (en millisecondes) à laquelle la mise en mémoire tampon doit commencer.
1. Utilisez la variable `replaceCurrentItem()` et `play()` méthodes de `MediaPlayer` pour commencer à jouer à partir de ce point.
1. Attente de l’état inactif et appel `replaceCurrentItem`.
1. Lire l’élément.

   * Si l’élément est chargé mais pas mis en mémoire tampon :

      1. Attendez l’état initialisé.
      1. Appeler `prepareToPlay()`.
      1. Attendez l’état PRÉPARÉ .
      1. Appeler `play()`.

   * Si l’élément est mis en mémoire tampon :

      1. Attendez l’événement préparé pour la mémoire tampon.
      1. Appeler `play()`.
