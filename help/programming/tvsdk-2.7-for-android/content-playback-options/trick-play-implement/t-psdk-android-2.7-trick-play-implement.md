---
description: Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuces, définissez le taux de lecture de MediaPlayer sur une valeur autre que 1.
title: Mise en oeuvre rapide de l’avance et du rembobinage
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Aperçu {#implement-fast-forward-and-rewind-overview}

Lorsque les utilisateurs avancent rapidement ou reviennent rapidement à travers le média, ils sont en mode de jeu de tour. Pour passer en mode de lecture par astuces, définissez le taux de lecture de MediaPlayer sur une valeur autre que 1.

Pour changer de vitesse, vous devez définir une valeur.

1. Passez du mode de lecture normal (1x) au mode de lecture fictive en définissant le taux sur `MediaPlayer` à une valeur autorisée.

       Rappelez-vous des informations suivantes :
   
   * La classe `MediaPlayerItem` définit les taux de lecture autorisés.
   * TVSDK sélectionne le taux autorisé le plus proche si le taux spécifié n’est pas autorisé.

      L’exemple suivant montre comment définir le taux de lecture interne du lecteur sur le taux demandé :

      ```
      import com.adobe.mediacore.MediaPlayer; 
      import com.adobe.mediacore.MediaPlayerItem; 
      import com.adobe.mediacore.MediaPlayerException; 
      import java.util.List; 
      import java.lang.Float; 
      
      private boolean setPlaybackRate(MediaPlayer player, float rate)  
        throws MediaPlayerException { 
          // Get list of playback rates that the media player supports 
          MediaPlayerItem item = player.getCurrentItem(); 
          if (item == null) return false; 
          List<Float> availableRates = player.getCurrentItem().getAvailablePlaybackRates(); 
      
          // Return false if requested rate is not supported 
          if (availableRates.indexOf(rate) == -1) return false; 
      
          // Otherwise set the playback rate to the requested rate  
          // (this can throw MediaPlayerException) 
          player.setRate(rate); 
          return true; 
      }
      ```

1. Vous pouvez éventuellement écouter les événements de changement de taux, qui vous avertissent lorsque vous demandez un changement de taux et lorsque le changement de taux se produit effectivement.

       TVSDK distribue les événements suivants liés au jeu vidéo :
   
   * `MediaPlayerEvent.RATE_SELECTED`, lorsque la  `rate` valeur change.

   * `MediaPlayerEvent.RATE_PLAYING`, lorsque la lecture reprend au rythme sélectionné.

      TVSDK distribue ces événements lorsque le lecteur revient du mode de lecture de l’astuce au mode de lecture normal.

