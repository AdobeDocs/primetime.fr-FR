---
description: Le SDK TVSDK informe le client du lecteur de la disponibilité des paramètres AVAsset internes availableMediaCaractéristiquesWithMediaSelectionOptions à l’aide de la notification PTMediaPlayerMediaSelectionOptionsAvailableNotification.
seo-description: Le SDK TVSDK informe le client du lecteur de la disponibilité des paramètres AVAsset internes availableMediaCaractéristiquesWithMediaSelectionOptions à l’aide de la notification PTMediaPlayerMediaSelectionOptionsAvailableNotification.
seo-title: Exposer les sous-titres
title: Exposer les sous-titres
uuid: 657ab9c7-b205-4d13-81a7-51bc8e7d5ee2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Exposer les sous-titres {#expose-subtitles}

Le SDK TVSDK informe le client du lecteur de la disponibilité des paramètres AVAsset internes availableMediaCaractéristiquesWithMediaSelectionOptions à l’aide de la notification PTMediaPlayerMediaSelectionOptionsAvailableNotification.

Vous pouvez accéder aux sous-titres disponibles par l&#39;intermédiaire de la `PTMediaPlayerItem` propriété `subtitlesOptions`.

Pour exposer les sous-titres :

1. Enregistrez le client en tant qu’écouteur pour la `PTMediaPlayerMediaSelectionOptionsAvailableNotification` notification.

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   Lorsque votre client reçoit cette notification, les sous-titres sont prêts dans le `PTMediaPlayerItem`.
1. Implémentez la `onMediaPlayerItemMediaSelectionOptionsAvailable` méthode comme dans l’exemple suivant :

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   Pour plus d’informations sur les autres pistes audio, voir [Alternate Audio](../alternate-audio/c-psdk-ios-1.4-alternate-audio.md).