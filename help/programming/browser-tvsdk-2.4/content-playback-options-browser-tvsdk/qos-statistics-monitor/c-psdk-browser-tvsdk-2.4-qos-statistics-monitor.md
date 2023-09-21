---
description: La qualité de service (QoS) offre une vue détaillée des performances du moteur vidéo. TVSDK du navigateur fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les appareils.
title: Statistiques de qualité du service
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Statistiques de qualité du service{#quality-of-service-statistics}

La qualité de service (QoS) offre une vue détaillée des performances du moteur vidéo. TVSDK du navigateur fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les appareils.

## Lecture de QOS, mise en mémoire tampon et statistiques sur les appareils {#read-qos-playback-buffering-and-device-statistics}

Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et d’appareil à partir de la classe QOSProvider .

La variable `QOSProvider` fournit diverses statistiques, notamment des informations sur la mise en mémoire tampon, les débits, les taux d’images, les données temporelles, etc.

1. Instanciation d’un lecteur multimédia
1. Créez un `QOSProvider` et joignez-la au lecteur multimédia.

   ```js
   // Create Media Player.qosProvider =  
         new AdobePSDK.QOSProvider(); 
   qosProvider.attachMediaPlayer(player);
   ```

1. (Facultatif) Lisez les statistiques de lecture.

   Une solution pour lire les statistiques de lecture consiste à disposer d’un minuteur qui récupère régulièrement les nouvelles valeurs QoS de la variable `QOSProvider`. Par exemple :

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

1. (Facultatif) Lisez les informations spécifiques à l’appareil.

   ```js
   // Show device information 
   DeviceInformation deviceInfo = new QOSProvider().deviceInformation; 
   console.log("OS: "+ deviceInfo.getOS()); 
   console.log("Width: "+ deviceInfo.getWidthPixels() +  
               "Height: "+ deviceInfo.getHeightPixels() );
   ```
