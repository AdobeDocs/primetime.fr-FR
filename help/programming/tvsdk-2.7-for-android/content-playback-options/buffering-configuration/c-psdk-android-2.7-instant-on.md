---
description: L’activation instantanée signifie qu’un ou plusieurs canaux sont préchargés. Lorsque les utilisateurs sélectionnent un canal ou changent de canal, le contenu est lu immédiatement. La mise en mémoire tampon est terminée au moment où l’utilisateur début regarder.
seo-description: L’activation instantanée signifie qu’un ou plusieurs canaux sont préchargés. Lorsque les utilisateurs sélectionnent un canal ou changent de canal, le contenu est lu immédiatement. La mise en mémoire tampon est terminée au moment où l’utilisateur début regarder.
seo-title: Instant activé
title: Instant activé
uuid: 7e14b779-2a36-4ff4-a365-9ac49a836ff3
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Instant activé {#instant-on}

L’activation instantanée signifie qu’un ou plusieurs canaux sont préchargés. Lorsque les utilisateurs sélectionnent un canal ou changent de canal, le contenu est lu immédiatement. La mise en mémoire tampon est terminée au moment où l’utilisateur début regarder.

Sans Instant On, TVSDK initialise le média à lire, mais ne début pas la mise en mémoire tampon du flux tant que l’application n’appelle pas `play`. L’utilisateur ne voit aucun contenu tant que la mise en mémoire tampon n’est pas terminée. Avec Instant On, vous pouvez lancer plusieurs instances de lecteur multimédia (ou de chargeur d’élément du lecteur multimédia) et les débuts TVSDK mettent immédiatement les flux en mémoire tampon. Lorsqu’un utilisateur modifie le canal et que le flux est mis en mémoire tampon correctement, il appelle immédiatement `play` la lecture du nouveau début de canal.

Bien qu’il n’existe aucune limite au nombre d’ `MediaPlayer` `MediaPlayerItemLoader` instances et d’instances que TVSDK peut exécuter, l’exécution d’un plus grand nombre d’instances consomme davantage de ressources. Les performances de l’application peuvent être affectées par le nombre d’instances en cours d’exécution. Pour plus d’informations sur `MediaPlayerItemLoader`, voir [Chargement d’une ressource multimédia dans le lecteur](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md)multimédia.

>[!IMPORTANT]
>
>TVSDK ne prend pas en charge un seul `QoSProvider` pour travailler à la fois `itemLoader` et `MediaPlayer`. Si le client utilise Instant On, l’application doit gérer deux instances QoS et gérer les deux instances pour les informations.

Pour plus d’informations sur `MediaPlayerItemLoader`MediaPlayerItemLoader [, voir](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md)Chargement d’une ressource multimédia.

## Ajouter une instance du fournisseur QoS à mediaPlayerItemLoader {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* Création et association d’un fournisseur QoS à une `mediaPlayerItemLoader` instance

   ```
   // Create an instance of QoSProvider  
   private QOSProvider _qosProvider = new QOSProvider(this._context);  
   
   // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
   // (before calling load API on mediaPlayerItemLoader instance)  
   _qosProvider.attachMediaPlayerItemLoader(this._loader); 
   ```

   Une fois que la lecture est début, utilisez le `_qosProvider` pour obtenir `timeToLoad` et `timeToPrepare` des données QoSdata. Les autres mesures de QoS peuvent être récupérées à l’aide des `QoSProvider` données jointes au `mediaPlayer`.

   Pour plus d’informations sur `MediaPlayerItemLoader`MediaPlayerItemLoader [, voir](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md#use-mediaplayeritemloader)Chargement d’une ressource multimédia.

## Configuration de la mise en mémoire tampon pour Instant On {#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDK fournit des méthodes et des états pour vous permettre d’utiliser Instant On avec une ressource multimédia.

>[!NOTE]
>
>Adobe recommande `MediaPlayerItemLoader` d’utiliser pour InstantOn. Pour utiliser `MediaPlayerItemLoader`, plutôt que `MediaPlayer`, voir media-resource-load-using-mediaplayeritemloader .

1. Vérifiez que la ressource est chargée et que le lecteur est prêt à la lire.
1. Avant d’appeler `play`, appelez `prepareBuffer` pour chaque `MediaPlayer` instance.

   >[!NOTE]
   >
   >`prepareBuffer` active la mise en mémoire tampon des débuts Instant On et TVSDK immédiatement et distribue le `BUFFERING_COMPLETED` événement lorsque la mémoire tampon est pleine.

   >[!TIP]
   >
   >Par défaut, `prepareBuffer` et `prepareToPlay` configurez le flux média pour qu’il soit lu en début dès le début. Pour début à une autre position, transmettez la position (en millisecondes) à `prepareToPlay`.

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

1. Lorsque vous recevez le `BUFFERING_COMPLETE` événement, début de lecture de l’élément ou affichage des commentaires visuels pour indiquer que le contenu est complètement mis en mémoire tampon.

   >[!NOTE]
   >
   >Si vous appelez `play`, la lecture doit commencer immédiatement.

