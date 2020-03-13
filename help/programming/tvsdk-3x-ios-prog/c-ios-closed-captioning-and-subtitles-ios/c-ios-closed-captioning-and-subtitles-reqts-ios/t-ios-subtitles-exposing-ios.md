---
description: Le SDK TVSDK informe le client du lecteur de la disponibilité des paramètres AVAsset internes availableMediaCaractéristiquesWithMediaSelectionOptions à l’aide de la notification PTMediaPlayerMediaSelectionOptionsAvailableNotification.
seo-description: Le SDK TVSDK informe le client du lecteur de la disponibilité des paramètres AVAsset internes availableMediaCaractéristiquesWithMediaSelectionOptions à l’aide de la notification PTMediaPlayerMediaSelectionOptionsAvailableNotification.
seo-title: Exposer les sous-titres
title: Exposer les sous-titres
uuid: 1cd8761f-6e6f-4017-9852-fa61f36197c5
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

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

   Pour plus d’informations sur les autres pistes audio, voir [Alternate Audio](../../alternate-audio/ios-3x-alternate-audio.md).