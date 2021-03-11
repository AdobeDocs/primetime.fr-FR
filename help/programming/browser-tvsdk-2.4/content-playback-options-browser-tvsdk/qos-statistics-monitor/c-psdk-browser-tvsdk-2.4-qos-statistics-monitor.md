---
description: La qualité de service (QoS) offre une vue détaillée sur les performances du moteur vidéo. Le navigateur TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
title: Statistiques sur la qualité des services
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 1%

---


# Statistiques sur la qualité du service{#quality-of-service-statistics}

La qualité de service (QoS) offre une vue détaillée sur les performances du moteur vidéo. Le navigateur TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.

## Lire les statistiques de lecture, de mise en mémoire tampon et de périphérique de QOS {#read-qos-playback-buffering-and-device-statistics}

Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et de périphérique à partir de la classe QOSProvider.

La classe `QOSProvider` fournit diverses statistiques, notamment des informations sur la mise en mémoire tampon, les débits, les débits d&#39;images, les données temporelles, etc.

1. Instanciez un lecteur multimédia.
1. Créez un objet `QOSProvider` et joignez-le au lecteur de médias.

   ```js
   // Create Media Player.qosProvider =  
         new AdobePSDK.QOSProvider(); 
   qosProvider.attachMediaPlayer(player);
   ```

1. (Facultatif) Lisez les statistiques de lecture.

   Une solution pour lire les statistiques de lecture consiste à disposer d’un minuteur, qui récupère périodiquement les nouvelles valeurs QoS du `QOSProvider`. Par exemple :

   ```js
   var qosTimer = (function () { 
       var ref = null, 
       qosChangeInterval = 500, // in milliseconds 
   
       startTimer = function () { 
           var playbackInformation = qosProvider.playbackInformation; 
        console.log("Frame rate", playbackInformation.frameRate); 
           console.log ("Dropped frames", playbackInformation.droppedFrameCount); 
           console.log ("Bitrate", playbackInformation.bitrate); 
           console.log ("Buffering time", playbackInformation.bufferingTime); 
           console.log ("Buffer length", playbackInformation.bufferLength); 
           console.log ("Buffer time", playbackInformation.bufferTime); 
           console.log ("Empty buffer count", playbackInformation.emptyBufferCount); 
           console.log ("Time to load", playbackInformation.timeToLoad); 
           console.log ("Time to start", playbackInformation.timeToStart); 
           ref = window.setTimeout(startTimer, qosChangeInterval); 
       }; 
   
       return { 
           start: function () { 
               if (ref !== null) { 
                   // don't start another timeout if one already exists. 
                   return; 
               } 
               startTimer(); 
           }, 
   
           stop: function () { 
               window.clearTimeout(ref); 
               ref = null; 
           } 
       };  
   })() 
   
   qosTimer.start(); 
   ```

1. (Facultatif) Lisez les informations spécifiques au périphérique.

   ```js
   // Show device information 
   DeviceInformation deviceInfo = new QOSProvider().deviceInformation; 
   console.log("OS: "+ deviceInfo.getOS()); 
   console.log("Width: "+ deviceInfo.getWidthPixels() +  
               "Height: "+ deviceInfo.getHeightPixels() );
   ```
