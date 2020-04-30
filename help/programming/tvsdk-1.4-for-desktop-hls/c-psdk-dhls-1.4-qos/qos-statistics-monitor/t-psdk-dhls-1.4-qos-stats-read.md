---
description: Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et de périphérique à partir de la classe QOSProvider.
seo-description: Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et de périphérique à partir de la classe QOSProvider.
seo-title: Lire les statistiques de lecture, de mise en mémoire tampon et de périphérique de QOS
title: Lire les statistiques de lecture, de mise en mémoire tampon et de périphérique de QOS
uuid: 5ee631fc-cd6f-4f35-8621-2ffdc51a57c7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Lire les statistiques de lecture, de mise en mémoire tampon et de périphérique de QOS{#read-qos-playback-buffering-and-device-statistics}

Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et de périphérique à partir de la classe QOSProvider.

La `QOSProvider` classe fournit diverses statistiques, notamment des informations sur la mise en mémoire tampon, les débits, les débits d&#39;images, les données temporelles, etc.

Il fournit également des informations sur le périphérique, telles que le fabricant, le modèle, le système d’exploitation, la version du SDK et la taille/densité d’écran.

1. Instanciez un lecteur multimédia.
1. Créez un `QOSProvider` objet et joignez-le au lecteur de médias.

   ```
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider; 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Facultatif) Lisez les statistiques de lecture.

   Une solution pour lire les statistiques de lecture consiste à disposer d’un minuteur, qui récupère périodiquement les nouvelles valeurs de QoS du `QOSProvider`. Par exemple :

   ```
   var qosTimer:Timer = new Timer(1000); // every 1 second  
   qosTimer.addEventListener(TimerEvent.Timer, onQoSTimer);  
   qosTimer.start(); 
   private function onQoSTimer(event:TimerEvent):void { 
       var playbackInformation:PlaybackInformation = _mediaQosProvider.getPlaybackInformation(); 
       qosInfo["Frame rate"] = playbackInformation.frameRate.toFixed();  
       qosInfo["Dropped frames"] = playbackInformation.droppedFrameCount.toFixed(); 
       qosInfo["Bitrate"] = playbackInformation.bitrate.toFixed(); 
       qosInfo["Bandwidth"] = playbackInformation.perceivedBandwidth; 
       qosInfo["Buffering time"] = playbackInformation.bufferingTime.toFixed(); 
       qosInfo["Buffer length"] = playbackInformation.bufferLength.toFixed();  
       qosInfo["Buffer time"] = playbackInformation.bufferTime.toFixed(); 
       qosInfo["Empty buffer count"] = playbackInformation.emptyBufferCount.toFixed();  
       qosInfo["Time to load"] = playbackInformation.timeToLoad.toFixed();  
       qosInfo["Time to start"] = playbackInformation.timeToStart.toFixed(); 
       qosView.update(qosInfo); 
   }
   ```

1. (Facultatif) Lisez les informations spécifiques au périphérique.

   ```
   // Show device information 
   var deviceInfo:DeviceInformation = new QOSProvider.deviceInformation; 
   qosInfo["deviceModel"] = deviceInfo.manufacturer +"-" + deviceInfo.model; 
   qosInfo["os"] = deviceInfo.os;  
   qosInfo["runtime"] = deviceInfo.runtimeVersion;  
   qosInfo["widthPixels"] = deviceInfo.widthPixels;  
   qosInfo["heightPixels"] = deviceInfo.heightPixels; 
   qosView.update(qosInfo); 
   ```

