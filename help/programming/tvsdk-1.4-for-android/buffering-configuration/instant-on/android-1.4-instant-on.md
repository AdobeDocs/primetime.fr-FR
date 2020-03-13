---
description: Le terme "instantané" fait référence au préchargement d’un ou de plusieurs  de sorte qu’un utilisateur qui sélectionne un ou qui change devoit le contenu lire immédiatement. La mise en mémoire tampon est déjà effectuée au moment où l’utilisateur  regarder.
seo-description: Le terme "instantané" fait référence au préchargement d’un ou de plusieurs  de sorte qu’un utilisateur qui sélectionne un ou qui change devoit le contenu lire immédiatement. La mise en mémoire tampon est déjà effectuée au moment où l’utilisateur  regarder.
seo-title: Instant le
title: Instant le
uuid: 4cb4d221-170f-46e8-af26-32f259377617
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Instant le {#instant-on}

Le terme &quot;instantané&quot; fait référence au préchargement d’un ou de plusieurs  de sorte qu’un utilisateur qui sélectionne un ou qui change devoit le contenu lire immédiatement. La mise en mémoire tampon est déjà effectuée au moment où l’utilisateur  regarder.

Sans instantané, TVSDK initialise le média à lire, mais ne pas la mise en mémoire tampon du flux jusqu’à ce que l’application appelle `play`. L’utilisateur ne voit aucun contenu tant que la mise en mémoire tampon n’est pas terminée. Instantanément, vous pouvez lancer plusieurs instances de lecteur multimédia (ou de chargeur d’élément du lecteur multimédia) et le TVSDK  mettre les flux en mémoire tampon immédiatement.

Lorsqu’un utilisateur modifie le et que le flux a été mis en mémoire tampon correctement, l’appel `play` au nouvel  de lecture  s’effectue immédiatement.

Bien qu’il n’existe aucune limite au nombre d’ `MediaPlayer` instances que TVSDK peut exécuter, l’exécution d’un plus grand nombre d’instances consomme plus de ressources. Les performances de l’application peuvent être affectées par le nombre d’instances en cours d’exécution. Pour plus d’informations sur ces instances, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).

## Configuration de la mise en mémoire tampon pour la lecture instantanée {#configure-buffering-for-instant-on-playback}

Instantanément activé, les utilisateurs peuvent changer de  et le de lecture  immédiatement sans délai d’attente. Lorsque vous activez l’activation instantanée, TVSDK met en mémoire tampon un ou plusieurs  avant le début de la lecture.

1. Vérifiez que la ressource a été chargée et qu’elle est prête à être lue en vérifiant que l’état est PRÉPARÉ.
1. Avant d’appeler `play`, appelez `prepareBuffer` pour chaque `MediaPlayer` instance.

   Cela active l’instantané, ce qui signifie que le TVSDK  la mise en mémoire tampon sans réellement lire la ressource multimédia. TVSDK distribue le `BUFFERING_COMPLETED` lorsque la mémoire tampon est pleine.

   >[!NOTE]
   >
   >Par défaut, `prepareBuffer` puis `prepareToPlay` configurez le flux média pour qu’il  de la lecture depuis le début. Pour  à une autre position, transmettez la position (en millisecondes) dans `prepareToPlay`.

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

1. Lorsque vous recevez le `BUFFERING_COMPLETE` ,  la lecture de l’élément ou affichez des commentaires visuels pour indiquer que le contenu est complètement mis en mémoire tampon.

   Si vous appelez `play`, la lecture doit commencer immédiatement.

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
