---
description: Le terme "instantané" fait référence au préchargement d’un ou de plusieurs canaux de sorte qu’un utilisateur qui sélectionne un canal ou qui change de canal voit la lecture immédiate du contenu. La mise en mémoire tampon est déjà effectuée au moment où l’utilisateur commence à regarder.
title: Instant on
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Instant on {#instant-on}

Le terme &quot;instantané&quot; fait référence au préchargement d’un ou de plusieurs canaux de sorte qu’un utilisateur qui sélectionne un canal ou qui change de canal voit la lecture immédiate du contenu. La mise en mémoire tampon est déjà effectuée au moment où l’utilisateur commence à regarder.

Sans instantanément, TVSDK initialise le média à lire, mais ne commence pas à mettre en mémoire tampon le flux jusqu’à ce que l’application appelle `play`. L’utilisateur ne voit aucun contenu tant que la mise en mémoire tampon n’est pas terminée. À l’instant présent, vous pouvez lancer plusieurs instances de lecteur multimédia (ou de chargeur d’éléments du lecteur multimédia), et TVSDK commence immédiatement à mettre en mémoire tampon les diffusions.

Lorsqu’un utilisateur modifie le canal et que la diffusion a été mise en mémoire tampon correctement, l’appel `play` sur le nouveau canal, la lecture démarre immédiatement.

Bien qu’il n’existe aucune limite au nombre de `MediaPlayer` les instances que TVSDK peut exécuter, l’exécution d’un plus grand nombre d’instances consomme plus de ressources. Les performances de l’application peuvent être affectées par le nombre d’instances en cours d’exécution. Pour plus d’informations sur ces instances, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).

## Configuration de la mise en mémoire tampon pour la lecture instantanée {#configure-buffering-for-instant-on-playback}

Dès qu’ils sont activés, les utilisateurs peuvent changer de canal et la lecture démarre immédiatement sans délai d’attente. Lorsque vous activez l’instantané, TVSDK met en mémoire tampon une ou plusieurs chaînes avant le début de la lecture.

1. Vérifiez que la ressource a été chargée et qu’elle est prête à être lue en vérifiant que l’état est PRÉPARÉ.
1. Avant d’appeler `play`, appel `prepareBuffer` pour chaque `MediaPlayer` instance.

   Cela permet d’activer instantanément, ce qui signifie que TVSDK commence la mise en mémoire tampon sans réellement lire la ressource multimédia. TVSDK distribue la variable `BUFFERING_COMPLETED` lorsque la mémoire tampon est pleine.

   >[!NOTE]
   >
   >Par défaut, `prepareBuffer` et `prepareToPlay` configurez le flux multimédia pour qu’il commence à être lu à partir du début. Pour commencer à une autre position, transmettez la position (en millisecondes) dans `prepareToPlay`.

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

1. Lorsque vous recevez la variable `BUFFERING_COMPLETE` , commencez à lire l’élément ou affichez un commentaire visuel pour indiquer que le contenu est entièrement mis en mémoire tampon.

   Si vous appelez `play`, la lecture doit commencer immédiatement.

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
