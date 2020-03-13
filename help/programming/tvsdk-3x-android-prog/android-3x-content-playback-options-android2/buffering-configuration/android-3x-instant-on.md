---
description: L’activation instantanée signifie qu’un ou plusieurs  sont préchargés. Lorsque l’utilisateur sélectionne un  ou change de, le contenu est lu immédiatement. La mise en mémoire tampon est terminée au moment où l’utilisateur  regarder.
seo-description: L’activation instantanée signifie qu’un ou plusieurs  sont préchargés. Lorsque l’utilisateur sélectionne un  ou change de, le contenu est lu immédiatement. La mise en mémoire tampon est terminée au moment où l’utilisateur  regarder.
seo-title: Instant activé
title: Instant activé
uuid: 5b1ceace-cae7-44c7-b4b9-d45078d58cc3
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# Instant activé {#instant-on}

L’activation instantanée signifie qu’un ou plusieurs  sont préchargés. Lorsque l’utilisateur sélectionne un  ou change de, le contenu est lu immédiatement. La mise en mémoire tampon est terminée au moment où l’utilisateur  regarder.

Sans Instant On, TVSDK initialise le média à lire, mais ne pas la mise en mémoire tampon du flux jusqu’à ce que l’application appelle `play`. L’utilisateur ne voit aucun contenu tant que la mise en mémoire tampon n’est pas terminée. Avec Instant On, vous pouvez lancer plusieurs instances de lecteur multimédia (ou de chargeur d’élément du lecteur multimédia) et le TVSDK  mettre les flux en mémoire tampon immédiatement. Lorsqu’un utilisateur modifie le et que le flux a été mis en mémoire tampon correctement, l’appel `play` au nouvel  de lecture  s’effectue immédiatement.

Bien qu’il n’existe aucune limite au nombre d’ `MediaPlayer` instances et `MediaPlayerItemLoader` d’instances que TVSDK peut exécuter, l’exécution d’un plus grand nombre d’instances consomme plus de ressources. Les performances de l’application peuvent être affectées par le nombre d’instances en cours d’exécution. Pour plus d’informations sur `MediaPlayerItemLoader`le lecteur [multimédia, voir](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md)Chargement d’une ressource multimédia dans le lecteur.

>[!IMPORTANT]
>
>TVSDK ne prend pas en charge un seul `QoSProvider` pour travailler avec `itemLoader` et `MediaPlayer`. Si le client utilise Instant On, l’application doit gérer deux instances QoS et les deux instances pour les informations.

Pour plus d’informations sur `MediaPlayerItemLoader`le chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader [, voir](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md)Chargement d’une ressource multimédia.

## Ajouter une instance du fournisseur QoS à mediaPlayerItemLoader {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* Création et association d’un fournisseur QoS à une `mediaPlayerItemLoader` instance

   ```
   // Create an instance of QoSProvider  
   private QOSProvider _qosProvider = new QOSProvider(this._context);  
   
   // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
   // (before calling load API on mediaPlayerItemLoader instance)  
   _qosProvider.attachMediaPlayerItemLoader(this._loader); 
   ```

   Une fois le de lecture , utilisez `_qosProvider` pour obtenir `timeToLoad` et `timeToPrepare` des données QoSdata. Les autres mesures de QoS peuvent être récupérées à l’aide de la `QoSProvider` section jointe au `mediaPlayer`.

   Pour plus d’informations sur `MediaPlayerItemLoader`le chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader [, voir](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md)Chargement d’une ressource multimédia.

## Configuration de la mise en mémoire tampon pour Instant On {#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDK fournit des méthodes et des états pour vous permettre d’utiliser Instant On avec une ressource multimédia.

>[!NOTE]
>
>Adobe recommande d’utiliser `MediaPlayerItemLoader` pour InstantOn. Pour utiliser `MediaPlayerItemLoader`, plutôt que `MediaPlayer`, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

1. Vérifiez que la ressource est chargée et que le lecteur est prêt à la lire.
1. Avant d’appeler `play`, appelez `prepareBuffer` pour chaque `MediaPlayer` instance.

   `prepareBuffer` active Instant On et le TVSDK  la mise en mémoire tampon immédiatement et distribue le  de lorsque la mémoire tampon est pleine. `BUFFERING_COMPLETED`

   >[!TIP]
   >
   >Par défaut, `prepareBuffer` puis `prepareToPlay` configurez le flux média pour qu’il  de la lecture depuis le début. Pour  à une autre position, transmettez la position (en millisecondes) à `prepareToPlay`.

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

1. Lorsque vous recevez le `BUFFERING_COMPLETE` ,  la lecture de l’élément ou affichez des commentaires visuels pour indiquer que le contenu est complètement mis en mémoire tampon.

   >[!NOTE]
   >
   >Si vous appelez `play`, la lecture doit commencer immédiatement.