---
description: La qualité de service (QoS) offre une vue détaillée sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
seo-description: La qualité de service (QoS) offre une vue détaillée sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
seo-title: Statistiques sur la qualité des services
title: Statistiques sur la qualité des services
uuid: b74cbc94-1d69-4b4b-b969-d0e985b4762b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Statistiques sur la qualité du service{#quality-of-service-statistics}

La qualité de service (QoS) offre une vue détaillée sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.

## Lire les statistiques de lecture, de mise en mémoire tampon et de périphérique de QOS {#section_9996406E2D814FA382B77E3041CB02BC}

Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et de périphérique à partir de la classe `PTQOSProvider`.

La classe `PTQOSProvider` fournit diverses statistiques, notamment des informations sur la mise en mémoire tampon, les débits, les débits d&#39;images, les données temporelles, etc.

Il fournit également des informations sur le périphérique, telles que le modèle, le système d’exploitation et l’ID du périphérique du fabricant.

>[!TIP]
>
>Vous ne pouvez pas modifier la taille de la mémoire tampon de lecture, mais vous pouvez contrôler l’état de la taille de la mémoire tampon pour le débogage ou l’analyse. `PTPlaybackInformation` inclut des propriétés telles que  `playbackBufferFull` et  `playbackLikelyToKeepUp`.

1. Instanciez un lecteur multimédia.
1. Créez un objet `PTQOSProvider` et joignez-le au lecteur de médias.

   Le constructeur `PTQOSProvider` prend en compte le contexte du lecteur afin de pouvoir récupérer des informations spécifiques au périphérique.

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. (Facultatif) Lisez les statistiques de lecture.

   Une solution pour lire les statistiques de lecture consiste à disposer d’un minuteur, tel qu’un `NSTimer`, qui récupère périodiquement les nouvelles valeurs QoS de `PTQOSProvider`. Par exemple :

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

