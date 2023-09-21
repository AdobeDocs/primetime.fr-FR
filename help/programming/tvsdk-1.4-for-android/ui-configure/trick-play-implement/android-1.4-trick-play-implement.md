---
description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de lecture de l’astuce. Pour passer en mode de lecture de l’astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.
title: Mise en oeuvre rapide en avant et en arrière
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Présentation {#implement-fast-forward-and-rewind-overview}

Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de lecture de l’astuce. Pour passer en mode de lecture de l’astuce, vous devez définir le taux de lecture de MediaPlayer sur une valeur autre que 1.

Pour changer de vitesse, vous devez définir une valeur.

1. Passer du mode de lecture normal (1x) au mode de lecture astucieux en définissant le taux sur la `MediaPlayer` à une valeur autorisée.

   * La variable `MediaPlayerItem` définit les taux de lecture autorisés.
   * TVSDK sélectionne le taux autorisé le plus proche si le taux spécifié n’est pas autorisé.

   Cet exemple définit le taux de lecture interne du lecteur sur le taux demandé.

   ```java
   import com.adobe.mediacore.MediaPlayer; 
   import com.adobe.mediacore.MediaPlayerItem; 
   import com.adobe.mediacore.MediaPlayerException; 
   import java.util.List; 
   import java.lang.Float; 
   
   private boolean setPlaybackRate(MediaPlayer player, float rate) throws MediaPlayerException  
   { 
       //Get list of playback rates that the media player supports 
       MediaPlayerItem item = player.getCurrentItem(); 
       if(item == null) return false; 
       List<Float> availableRates = player.getCurrentItem().getAvailablePlaybackRates(); 
   
       //Return false if requested rate is not supported 
       if(availableRates.indexOf(rate) == -1) return false; 
   
       //Otherwise set the playback rate to the requested rate  
       //(this can throw MediaPlayerException) 
       player.setRate(rate); 
       return true; 
   }
   ```

1. Vous pouvez éventuellement écouter les événements de changement de taux, qui vous permettent de savoir quand vous avez demandé un changement de taux et quand un changement de taux se produit réellement.

       TVSDK distribue les événements suivants liés à la lecture de l’astuce :
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` lorsque la variable `rate` change de valeur.

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` lorsque la lecture reprend au rythme sélectionné.

     TVSDK distribue ces deux événements lorsque le lecteur revient du mode de lecture de l’astuce au mode de lecture normal.
