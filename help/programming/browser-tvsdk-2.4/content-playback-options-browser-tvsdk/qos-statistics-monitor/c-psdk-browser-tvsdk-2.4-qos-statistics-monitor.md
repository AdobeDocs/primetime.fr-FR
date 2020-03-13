---
description: Qualité du service  (QoS)  un détaillé sur les performances du moteur vidéo. Le navigateur TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
seo-description: Qualité du service  (QoS)  un détaillé sur les performances du moteur vidéo. Le navigateur TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
seo-title: Statistiques sur la qualité du service
title: Statistiques sur la qualité du service
uuid: e4bb2617-d8a7-4da7-b669-d6ffab2864bb
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Statistiques sur la qualité du service{#quality-of-service-statistics}

Qualité du service  (QoS)  un détaillé sur les performances du moteur vidéo. Le navigateur TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.

## Lecture des statistiques de lecture, de mise en mémoire tampon et de périphérique QOS {#read-qos-playback-buffering-and-device-statistics}

Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et de périphérique à partir de la classe QOSProvider.

La `QOSProvider` classe fournit diverses statistiques, notamment des informations sur la mise en mémoire tampon, les débits, les débits d’images, les données temporelles, etc.

1. Instanciez un lecteur multimédia.
1. Créez un `QOSProvider` objet et joignez-le au lecteur de médias.

   ```js
   // Create Media Player.qosProvider =  
         new AdobePSDK.QOSProvider(); 
   qosProvider.attachMediaPlayer(player);
   ```

1. (Facultatif) Lisez les statistiques de lecture.

   Une solution pour lire les statistiques de lecture consiste à disposer d’un minuteur, qui récupère régulièrement les nouvelles valeurs de la qualité de service `QOSProvider`. Par exemple :

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
