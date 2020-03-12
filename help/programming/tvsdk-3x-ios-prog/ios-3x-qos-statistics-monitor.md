---
description: Qualité du service  (QoS)  un détaillé sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
seo-description: Qualité du service  (QoS)  un détaillé sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
seo-title: Statistiques sur la qualité du service
title: Statistiques sur la qualité du service
uuid: c08c1031-616a-4776-92e2-1c405467689b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Statistiques sur la qualité du service {#quality-of-service-statistics}

Qualité du service  (QoS)  un détaillé sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.

## Lecture des statistiques de lecture, de mise en mémoire tampon et de périphérique QOS {#section_9996406E2D814FA382B77E3041CB02BC}

Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et de périphérique à partir de la `PTQOSProvider` classe.

La `PTQOSProvider` classe fournit diverses statistiques, notamment des informations sur la mise en mémoire tampon, les débits, les débits d’images, les données temporelles, etc.

Il fournit également des informations sur le périphérique, telles que le modèle, le système d’exploitation et l’ID du périphérique du fabricant.

>[!TIP]
>
>Vous ne pouvez pas modifier la taille de la mémoire tampon de lecture, mais vous pouvez contrôler l’état de la taille de la mémoire tampon pour le débogage ou  . `PTPlaybackInformation` inclut des propriétés telles que `playbackBufferFull` et `playbackLikelyToKeepUp`.

1. Instanciez un lecteur multimédia.
1. Créez un `PTQOSProvider` objet et joignez-le au lecteur de médias.

   Le `PTQOSProvider` constructeur prend un contexte de lecteur afin de pouvoir récupérer des informations spécifiques au périphérique.

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. (Facultatif) Lisez les statistiques de lecture.

   Une solution pour lire les statistiques de lecture consiste à disposer d’un minuteur, tel qu’un `NSTimer`, qui récupère périodiquement les nouvelles valeurs de la qualité de service `PTQOSProvider`. Par exemple :

   ```
   - (void)printPlaybackInfoLog { 
       PTPlaybackInformation *playbackInfo = qosProvider.playbackInformation;  
       if (playbackInfo) { 
           // For example: 
           NSString *infoLog = [NSString stringWithFormat:@"observedBitrate :  
                                  %f\n",playbackInfo.observedBitrate]; 
           [consoleView logMessage:@"====%@\n\n",infoLog]; 
       } 
   }
   ```

1. (Facultatif) Lisez les informations spécifiques au périphérique.

   ```
    PTDeviceInformation *devInfo = qosProvider.deviceInformation; 
   if (devInfo) { 
       [consoleView logMessage:@"=== qosDeviceInfo:==\n os =%@\n model =  
          %@\n id =%@\n\n", devInfo.os, devInfo.model, devInfo.id]; 
   } 
   [NSTimer scheduledTimerWithTimeInterval:2.0 target:self  
      selector:@selector(printPlaybackInfoLog) userInfo:nil repeats:YES];
   ```
