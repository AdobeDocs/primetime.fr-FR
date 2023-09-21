---
description: La qualité de service (QoS) offre une vue détaillée des performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les appareils.
title: Statistiques de qualité du service
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Statistiques de qualité du service{#quality-of-service-statistics}

La qualité de service (QoS) offre une vue détaillée des performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les appareils.

## Lecture de QOS, mise en mémoire tampon et statistiques sur les appareils {#section_9996406E2D814FA382B77E3041CB02BC}

Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et d’appareil à partir du `PTQOSProvider` classe .

La variable `PTQOSProvider` fournit diverses statistiques, notamment des informations sur la mise en mémoire tampon, les débits, les taux d’images, les données temporelles, etc.

Il fournit également des informations sur l’appareil, telles que le modèle, le système d’exploitation et l’identifiant de l’appareil du fabricant.

>[!TIP]
>
>Vous ne pouvez pas modifier la taille de la mémoire tampon de lecture, mais vous pouvez surveiller l’état de la taille de la mémoire tampon pour le débogage ou l’analyse. `PTPlaybackInformation` inclut des propriétés telles que `playbackBufferFull` et `playbackLikelyToKeepUp`.

1. Instanciation d’un lecteur multimédia
1. Créez un `PTQOSProvider` et joignez-la au lecteur multimédia.

   La variable `PTQOSProvider` le constructeur utilise un contexte du lecteur afin de pouvoir récupérer des informations spécifiques à l’appareil.

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. (Facultatif) Lisez les statistiques de lecture.

   Une solution pour lire les statistiques de lecture consiste à disposer d’un minuteur, tel qu’une `NSTimer`, qui récupère régulièrement les nouvelles valeurs QoS de la variable `PTQOSProvider`. Par exemple :

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

1. (Facultatif) Lisez les informations spécifiques à l’appareil.

   ```
    PTDeviceInformation *devInfo = qosProvider.deviceInformation; 
   if (devInfo) { 
       [consoleView logMessage:@"=== qosDeviceInfo:==\n os =%@\n model =  
          %@\n id =%@\n\n", devInfo.os, devInfo.model, devInfo.id]; 
   } 
   [NSTimer scheduledTimerWithTimeInterval:2.0 target:self  
      selector:@selector(printPlaybackInfoLog) userInfo:nil repeats:YES];
   ```
