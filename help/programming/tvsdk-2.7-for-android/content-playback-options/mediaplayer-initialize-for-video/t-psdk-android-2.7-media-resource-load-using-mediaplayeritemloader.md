---
description: L’utilisation de MediaPlayerItemLoader permet d’obtenir des informations sur un flux média sans instancier une instance MediaPlayer. Cela s’avère particulièrement utile dans les flux de mise en mémoire tampon afin que la lecture puisse commencer sans délai.
seo-description: L’utilisation de MediaPlayerItemLoader permet d’obtenir des informations sur un flux média sans instancier une instance MediaPlayer. Cela s’avère particulièrement utile dans les flux de mise en mémoire tampon afin que la lecture puisse commencer sans délai.
seo-title: Chargement d'une ressource multimédia à l'aide de MediaPlayerItemLoader
title: Chargement d'une ressource multimédia à l'aide de MediaPlayerItemLoader
uuid: 43ca2470-1fd2-4f66-94fe-a12ed17b52d7
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Charger une ressource multimédia à l&#39;aide de MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

L’utilisation de MediaPlayerItemLoader permet d’obtenir des informations sur un flux média sans instancier une instance MediaPlayer. Cela s’avère particulièrement utile dans les flux de mise en mémoire tampon afin que la lecture puisse commencer sans délai.

La classe `MediaPlayerItemLoader` permet d&#39;échanger une ressource média pour l&#39;actuelle `MediaPlayerItem` sans attacher une vue à une instance `MediaPlayer`, ce qui affecterait des ressources matérielles de décodage vidéo. Des étapes supplémentaires sont nécessaires pour le contenu protégé par DRM, mais ce manuel ne les décrit pas.

>[!IMPORTANT]
>
>TVSDK ne prend pas en charge un seul `QoSProvider` pour fonctionner avec `itemLoader` et `MediaPlayer`. Si votre application utilise Instant On, elle doit gérer deux instances `QoS` et gérer les deux instances pour les informations. Voir [Instantané](../../content-playback-options/buffering-configuration/c-psdk-android-2.7-instant-on.md) pour plus d&#39;informations.

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
   >Créez une instance distincte de `MediaPlayerItemLoader` pour chaque ressource. N&#39;utilisez pas une instance `MediaPlayerItemLoader` pour charger plusieurs ressources.

1. Implémentez la classe `ItemLoaderListener` pour recevoir des notifications de l&#39;instance `MediaPlayerItemLoader`.

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

   Dans le rappel `onLoadComplete()`, effectuez l&#39;une des opérations suivantes :

   * Assurez-vous que tout ce qui peut avoir une incidence sur la mise en mémoire tampon, par exemple, la sélection de pistes WebVTT ou audio, est terminé et appelez `prepareBuffer()` pour profiter de l&#39;instant présent.
   * Joignez l’élément à l’instance `MediaPlayer` en utilisant `replaceCurrentItem()`.

   Si vous appelez `prepareBuffer()`, vous recevez le événement BUFFER_PREPARED dans votre gestionnaire `onBufferPrepared` une fois la préparation terminée.

1. Appelez `load` sur l&#39;instance `MediaPlayerItemLoader` et transmettez la ressource à charger, et éventuellement l&#39;ID de contenu, ainsi qu&#39;une instance `MediaPlayerItemConfig`.

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. Pour mettre en mémoire tampon à partir d&#39;un point autre que le début du flux, appelez `prepareBuffer()` avec la position (en millisecondes) à laquelle la mise en mémoire tampon du début doit être effectuée.
1. Utilisez les méthodes `replaceCurrentItem()` et `play()` de `MediaPlayer` pour début la lecture à partir de ce point.
1. Attendez l&#39;état inactif et appelez `replaceCurrentItem`.
1. Lire l’élément.

   * Si l&#39;élément est chargé mais pas mis en mémoire tampon :

      1. Attendez l’état initialisé.
      1. Appelez `prepareToPlay()`.
      1. Attendez l’état PRÉPARÉ.
      1. Appelez `play()`.
   * Si l&#39;élément est mis en mémoire tampon :

      1. Attendez le événement préparé pour la mémoire tampon.
      1. Appelez `play()`.