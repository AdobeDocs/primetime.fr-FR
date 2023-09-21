---
description: Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et d’appareil à partir de la classe QOSProvider .
title: Lecture de QOS, mise en mémoire tampon et statistiques sur les appareils
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Lecture de QOS, mise en mémoire tampon et statistiques sur les appareils{#read-qos-playback-buffering-and-device-statistics}

Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et d’appareil à partir de la classe QOSProvider .

La variable `QOSProvider` fournit diverses statistiques, notamment des informations sur la mise en mémoire tampon, les débits, les taux d’images, les données temporelles, etc.

Il fournit également des informations sur l’appareil, telles que le fabricant, le modèle, le système d’exploitation, la version du SDK et la taille/densité d’écran.

1. Instanciation d’un lecteur multimédia
1. Créez un `QOSProvider` et joignez-la au lecteur multimédia.

   ```
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider; 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Facultatif) Lisez les statistiques de lecture.

   Une solution pour lire les statistiques de lecture consiste à disposer d’un minuteur qui récupère régulièrement les nouvelles valeurs QoS de la variable `QOSProvider`. Par exemple :

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

1. (Facultatif) Lisez les informations spécifiques à l’appareil.

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

