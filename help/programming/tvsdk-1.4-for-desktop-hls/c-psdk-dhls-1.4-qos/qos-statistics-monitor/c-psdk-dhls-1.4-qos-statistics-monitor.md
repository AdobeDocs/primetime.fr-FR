---
description: La qualité de service (QoS) offre une vue détaillée des performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les appareils.
title: Statistiques de qualité du service
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Statistiques de qualité du service {#quality-of-service-statistics}

La qualité de service (QoS) offre une vue détaillée des performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les appareils.

TVSDK fournit également des informations sur les ressources téléchargées suivantes :

* Lecture/fichiers manifestes
* Fragments de fichier
* Informations de tracking des fichiers

## Suivi au niveau du fragment à l’aide des informations de chargement {#track-at-the-fragment-level-using-load-information}

Vous pouvez lire des informations sur la qualité du service (QoS) relatives aux ressources téléchargées, telles que les fragments et les traces, à partir de la classe LoadInformation .

1. Mettez en oeuvre le `onLoadInformationAvailable` écouteur d’événement de rappel.

   ```
   private function onLoadInformationAvailable(event:LoadInformationEvent):void { 
       var loadInformation:LoadInformation = event.loadInformation; 
       // process the load information here     
   }
   ```

1. Enregistrez l’écouteur d’événement, que TVSDK appelle chaque fois qu’un fragment est téléchargé.

   ```
   player.addEventListener(LoadInformationEvent.LOAD_INFORMATION_AVAILABLE,  
                                    onLoadInformationAvailable);
   ```

1. Lisez les données présentant un intérêt dans la `LoadInformation` qui est transmis au rappel.

   <table id="table_75E61A2EB25E435DB631166A7FF64757"> 
   <thead> 
   <tr> 
      <th colname="col01" class="entry"> Propriété </th> 
      <th colname="col1" class="entry"> Type </th> 
      <th colname="col2" class="entry"> Description </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col01"> <span class="codeph"> downloadDuration </span> </td> 
      <td colname="col1"> <p>Nombre </p> </td> 
      <td colname="col2"> <p>Durée du téléchargement en millisecondes. </p> <p>TVSDK ne fait pas la distinction entre le temps nécessaire au client pour se connecter au serveur et le temps nécessaire pour télécharger le fragment complet. Par exemple, si le téléchargement d’un segment de 10 Mo prend 8 secondes, TVSDK fournit ces informations, mais ne vous indique pas qu’il a fallu 4 secondes jusqu’au premier octet et 4 secondes supplémentaires pour télécharger l’intégralité du fragment. </p> </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration </span> </td> 
      <td colname="col1"> <p>Nombre </p> </td> 
      <td colname="col2"> Durée du média des fragments téléchargés en millisecondes. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> size </span> </td> 
      <td colname="col1"> <p>Nombre </p> </td> 
      <td colname="col2"> Taille de la ressource téléchargée en octets. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex </span> </td> 
      <td colname="col1"> <p>int </p> </td> 
      <td colname="col2"> Index de la piste correspondante, s’il est connu ; dans le cas contraire, 0. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackName </span> </td> 
      <td colname="col1"> <p>Chaîne </p> </td> 
      <td colname="col2"> Nom de la piste correspondante, s’il est connu ; dans le cas contraire, nul. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackType </span> </td> 
      <td colname="col1"> <p>Chaîne </p> </td> 
      <td colname="col2"> Le type de la piste correspondante, s’il est connu ; dans le cas contraire, nul. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> type </span> </td> 
      <td colname="col1"> <p>Chaîne </p> </td> 
      <td colname="col2"> Téléchargement de TVSDK. L’une des options suivantes : 
      <ul id="ul_FA02F42D109344F4866073908CA4E835"> 
      <li id="li_0E2D3EBCAB58477FB5EA526C54FACFFB">MANIFEST - Une liste de lecture/un manifeste </li> 
      <li id="li_D7894C2F0CB64C909C6398288EA5683A">FRAGMENT - Un fragment </li> 
      <li id="li_4D4FEDB7704C411B80891B5028B0C20E">TRACK : fragment associé à un suivi spécifique. </li> 
      </ul> Il peut arriver qu’il ne soit pas possible de détecter le type de ressource. Si cela se produit, le fichier est renvoyé. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> url </span> </td> 
      <td colname="col1"> <p>Chaîne </p> </td> 
      <td colname="col2"> URL qui pointe vers la ressource téléchargée. </td> 
   </tr> 
   </tbody> 
   </table>

## Lecture de QOS, mise en mémoire tampon et statistiques sur les appareils {#read-qos-playback-buffering-and-device-statistics}

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
