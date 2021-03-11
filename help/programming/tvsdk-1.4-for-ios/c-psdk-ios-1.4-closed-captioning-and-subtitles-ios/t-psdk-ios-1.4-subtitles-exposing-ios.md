---
description: Le SDK TVSDK informe le client du lecteur de la disponibilité de la variable availableMediaCharacteristicsWithMediaSelectionOptions du fichier AVAsset interne en utilisant la notification PTMediaPlayerMediaSelectionOptionsAvailableNotification.
title: Exposer les sous-titres
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Exposer les sous-titres {#expose-subtitles}

Le SDK TVSDK informe le client du lecteur de la disponibilité de la variable availableMediaCharacteristicsWithMediaSelectionOptions du fichier AVAsset interne en utilisant la notification PTMediaPlayerMediaSelectionOptionsAvailableNotification.

Vous pouvez accéder aux sous-titres disponibles par l&#39;intermédiaire de la propriété `subtitlesOptions`  de la propriété `PTMediaPlayerItem`.

Pour exposer les sous-titres :

1. Enregistrez le client en tant que processus d’écoute pour la notification `PTMediaPlayerMediaSelectionOptionsAvailableNotification`.

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   Lorsque votre client reçoit cette notification, les sous-titres sont prêts dans le `PTMediaPlayerItem`.
1. Implémentez la méthode `onMediaPlayerItemMediaSelectionOptionsAvailable` comme dans l&#39;exemple suivant :

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   Pour plus d&#39;informations sur les pistes audio de remplacement, voir [Autre audio](../alternate-audio/c-psdk-ios-1.4-alternate-audio.md).