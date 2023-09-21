---
description: Le TVSDK informe votre client de lecteur de la disponibilité de l’option availableMediaCharacterlorsWithMediaSelectionOptions de la visionneuse interne AVAediaPlayerMediaSelectionOptionsAvailableNotification en utilisant la notification PTMediaPlayerMediaSelectionNotification .
title: Exposer les sous-titres
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Exposer les sous-titres {#expose-subtitles}

Le TVSDK informe votre client de lecteur de la disponibilité de l’option availableMediaCharacterlorsWithMediaSelectionOptions de la visionneuse interne AVAediaPlayerMediaSelectionOptionsAvailableNotification en utilisant la notification PTMediaPlayerMediaSelectionNotification .

Vous pouvez accéder aux sous-titres disponibles à l’aide du `PTMediaPlayerItem` de propriété `subtitlesOptions`.

Pour exposer des sous-titres :

1. Enregistrez le client en tant qu’écouteur pour le `PTMediaPlayerMediaSelectionOptionsAvailableNotification` notification.

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   Lorsque votre client reçoit cette notification, les sous-titres sont prêts dans la `PTMediaPlayerItem`.
1. Mettez en oeuvre le `onMediaPlayerItemMediaSelectionOptionsAvailable` similaire à l’exemple suivant :

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   Pour plus d’informations sur les autres pistes audio, voir  [Autre audio](../../alternate-audio/ios-3x-alternate-audio.md).
