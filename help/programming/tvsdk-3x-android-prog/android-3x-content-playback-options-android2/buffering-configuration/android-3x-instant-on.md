---
description: L’activation de l’instantané signifie qu’un ou plusieurs canaux sont préchargés. Lorsque les utilisateurs sélectionnent un canal ou changent de canaux, le contenu est lu immédiatement. La mise en mémoire tampon est terminée au moment où l’utilisateur commence à regarder.
title: Instant activé
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Instant activé {#instant-on}

L’activation de l’instantané signifie qu’un ou plusieurs canaux sont préchargés. Lorsque les utilisateurs sélectionnent un canal ou changent de canaux, le contenu est lu immédiatement. La mise en mémoire tampon est terminée au moment où l’utilisateur commence à regarder.

Sans Instant On, TVSDK initialise le média à lire, mais ne commence pas à mettre en mémoire tampon le flux jusqu’à ce que l’application appelle `play`. L’utilisateur ne voit aucun contenu tant que la mise en mémoire tampon n’est pas terminée. Instant On, vous pouvez lancer plusieurs instances de lecteur multimédia (ou de chargeur d’éléments du lecteur multimédia), et TVSDK commence immédiatement à mettre en mémoire tampon les diffusions. Lorsqu’un utilisateur modifie le canal et que la diffusion a été mise en mémoire tampon correctement, l’appel `play` sur le nouveau canal, la lecture démarre immédiatement.

Bien qu’il n’existe aucune limite au nombre de `MediaPlayer` et `MediaPlayerItemLoader` les instances que TVSDK peut exécuter, l’exécution d’un plus grand nombre d’instances consomme plus de ressources. Les performances de l’application peuvent être affectées par le nombre d’instances en cours d’exécution. Pour plus d’informations sur `MediaPlayerItemLoader`, voir [Chargement d’une ressource multimédia dans le lecteur multimédia](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md).

>[!IMPORTANT]
>
>TVSDK ne prend pas en charge une seule `QoSProvider` pour travailler avec les deux `itemLoader` et `MediaPlayer`. Si le client utilise Instant On, l’application doit gérer deux instances QoS et gérer les deux instances pour obtenir les informations.

Pour plus d’informations sur `MediaPlayerItemLoader`, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

## Ajout d’une instance de fournisseur QoS à mediaPlayerItemLoader {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* Création et association d’un fournisseur QoS à un `mediaPlayerItemLoader` instance

  ```
  // Create an instance of QoSProvider  
  private QOSProvider _qosProvider = new QOSProvider(this._context);  
  
  // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
  // (before calling load API on mediaPlayerItemLoader instance)  
  _qosProvider.attachMediaPlayerItemLoader(this._loader); 
  ```

  Une fois la lecture lancée, utilisez la méthode `_qosProvider` pour obtenir `timeToLoad` et `timeToPrepare` QoSdata. Les autres mesures QoS peuvent être récupérées à l’aide de la variable `QoSProvider` joint au `mediaPlayer`.

  Pour plus d’informations sur `MediaPlayerItemLoader`, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

## Configuration de la mise en mémoire tampon pour Instant On {#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDK fournit des méthodes et des états pour vous permettre d’utiliser Instant On avec une ressource multimédia.

>[!NOTE]
>
>Adobe recommande d’utiliser `MediaPlayerItemLoader` pour InstantOn. Pour utiliser `MediaPlayerItemLoader`, plutôt que `MediaPlayer`, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

1. Vérifiez que la ressource a été chargée et que le lecteur est prêt à la lire.
1. Avant d’appeler `play`, appel `prepareBuffer` pour chaque `MediaPlayer` instance.

   `prepareBuffer` active Instant On, et TVSDK commence immédiatement la mise en mémoire tampon et distribue la variable `BUFFERING_COMPLETED` lorsque la mémoire tampon est pleine.

   >[!TIP]
   >
   >Par défaut, `prepareBuffer` et `prepareToPlay` configurez le flux multimédia pour qu’il commence à être lu à partir du début. Pour commencer à une autre position, transmettez la position (en millisecondes) à `prepareToPlay`.

   ```
   @Override 
   public void onStatusChanged(MediaPlayerStatus status) { 
       switch (status) { 
           case INITIALIZED: 
               // This example starts 5 seconds into the stream. 
               mediaPlayer.prepareToPlay(5000); 
               break; 
           case PREPARING: 
               break; 
           case PREPARED: 
               mediaPlayer.prepareBuffer(); 
               break; 
           ... 
       } 
   }
   ```

1. Lorsque vous recevez la variable `BUFFERING_COMPLETE` , commencez à lire l’élément ou affichez un commentaire visuel pour indiquer que le contenu est entièrement mis en mémoire tampon.

   >[!NOTE]
   >
   >Si vous appelez `play`, la lecture doit commencer immédiatement.
