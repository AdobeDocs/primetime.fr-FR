---
description: Le terme "instantané" désigne le préchargement d’un ou de plusieurs canaux afin qu’un utilisateur qui sélectionne un canal ou change de canal voit le contenu s’afficher immédiatement. La mise en mémoire tampon est déjà effectuée au moment où l’utilisateur début regarder.
seo-description: Le terme "instantané" désigne le préchargement d’un ou de plusieurs canaux afin qu’un utilisateur qui sélectionne un canal ou change de canal voit le contenu s’afficher immédiatement. La mise en mémoire tampon est déjà effectuée au moment où l’utilisateur début regarder.
seo-title: Instant le
title: Instant le
uuid: 4cb4d221-170f-46e8-af26-32f259377617
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Instant le {#instant-on}

Le terme &quot;instantané&quot; désigne le préchargement d’un ou de plusieurs canaux afin qu’un utilisateur qui sélectionne un canal ou change de canal voit le contenu s’afficher immédiatement. La mise en mémoire tampon est déjà effectuée au moment où l’utilisateur début regarder.

Sans instantané, TVSDK initialise le média à lire, mais ne début pas la mise en mémoire tampon du flux jusqu’à ce que l’application appelle `play`. L’utilisateur ne voit aucun contenu tant que la mise en mémoire tampon n’est pas terminée. Instantanément, vous pouvez lancer plusieurs instances de lecteur multimédia (ou de chargeur d’élément du lecteur multimédia) et les débuts TVSDK mettent immédiatement les flux en mémoire tampon.

Lorsqu’un utilisateur modifie le canal et que le flux est mis en mémoire tampon correctement, il appelle immédiatement `play` la lecture du nouveau début de canal.

Bien qu’il n’existe aucune limite au nombre d’ `MediaPlayer` instances que TVSDK peut exécuter, l’exécution d’un plus grand nombre d’instances consomme davantage de ressources. Les performances de l’application peuvent être affectées par le nombre d’instances en cours d’exécution. Pour plus d’informations sur ces instances, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).

## Configuration de la mise en mémoire tampon pour une lecture instantanée {#configure-buffering-for-instant-on-playback}

Dès qu’il est activé, les utilisateurs peuvent changer de canal et de début de lecture immédiatement sans délai d’attente. Lorsque vous activez l’instantané, TVSDK met en mémoire tampon un ou plusieurs canaux avant le début de la lecture.

1. Vérifiez que la ressource est chargée et prête à être lue en vérifiant que l&#39;état est PRÉPARÉ.
1. Avant d’appeler `play`, appelez `prepareBuffer` pour chaque `MediaPlayer` instance.

   Cela active l&#39;instantané, ce qui signifie que TVSDK début la mise en mémoire tampon sans réellement lire la ressource média. TVSDK distribue le `BUFFERING_COMPLETED` événement lorsque la mémoire tampon est pleine.

   >[!NOTE]
   >
   >Par défaut, `prepareBuffer` et `prepareToPlay` configurez le flux média pour qu’il soit lu en début dès le début. Pour début à une autre position, transmettez la position (en millisecondes) en `prepareToPlay`.

   ```java
   @Override 
   public void onStateChanged(MediaPlayer.PlayerState state,  
                              MediaPlayerNotification notification) { 
       switch (state) { 
           case INITIALIZED: 
               // By default, prepareToPlay and prepareBuffer buffer and start playing 
               // from the beginning of the stream. To start at another position, 
               // pass it into prepareToPlay. This example starts 5 seconds into the stream. 
               _mediaPlayer.prepareToPlay(5000); 
               break; 
           case PREPARING: 
               break; 
           case PREPARED: 
               _mediaPlayer.prepareBuffer(); 
               break; 
           ... 
       } 
   }
   ```

1. Lorsque vous recevez le `BUFFERING_COMPLETE` événement, début de lecture de l’élément ou affichage des commentaires visuels pour indiquer que le contenu est complètement mis en mémoire tampon.

   Si vous appelez `play`, la lecture doit commencer immédiatement.

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
