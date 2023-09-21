---
description: La qualité de service (QoS) offre une vue détaillée des performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les appareils.
title: Statistiques de qualité du service
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Statistiques de qualité du service {#quality-of-service-statistics}

La qualité de service (QoS) offre une vue détaillée des performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les appareils.

TVSDK fournit également des informations sur les ressources téléchargées suivantes :

* Lecture/fichiers manifestes
* Fragments de fichier
* Informations de tracking des fichiers

## Suivi au niveau du fragment à l’aide des informations de chargement {#section_4439D91E8EDC45588EF1D7BE25697350}

Vous pouvez lire des informations sur la qualité du service (QoS) relatives aux ressources téléchargées, telles que des fragments et des traces, à partir de la page `LoadInformation` classe .

1. Mettez en oeuvre et enregistrez le `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` écouteur d’événement.
1. Appeler `event.getLoadInformation()` pour lire les données pertinentes de la `event` qui est transmis au rappel.

   >[!NOTE]
   >
   >Pour en savoir plus sur `LoadInformation`, voir [2.7 pour Android (Java)](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/index.html) Documentation API.

## Lecture de QOS, mise en mémoire tampon et statistiques sur les appareils {#section_D21722600F324E67A9F06234D338B243}

Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et d’appareil à partir du `QOSProvider` classe .

La variable `QOSProvider` fournit diverses statistiques, notamment des informations sur la mise en mémoire tampon, les débits, les taux d’images, les données temporelles, etc. Il fournit également des informations sur l’appareil, telles que le fabricant, le modèle, le système d’exploitation, la version du SDK, l’identifiant de l’appareil et la taille/densité d’écran.

1. Instanciation d’un lecteur multimédia
1. Créez un `QOSProvider` et joignez-la au lecteur multimédia.

   La variable `QOSProvider` le constructeur utilise un contexte du lecteur afin de pouvoir récupérer des informations spécifiques à l’appareil.

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Facultatif) Lisez les statistiques de lecture.

   Une solution pour lire les statistiques de lecture consiste à disposer d’un minuteur qui récupère régulièrement les nouvelles valeurs QoS de la variable `QOSProvider`.

   Par exemple :

   ```java
   _playbackClock = new Clock(PLAYBACK_CLOCK, 1000); // every 1 second 
   _playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           getActivity().runOnUiThread(new Runnable() { 
               @Override 
               public void run() { 
                   PlaybackInformation playbackInformation =  
                     _mediaQosProvider.getPlaybackInformation();  
                   setQosItem("Frame rate", (int) playbackInformation.getFrameRate());  
                   setQosItem("Dropped frames", (int) playbackInformation.getDroppedFrameCount()); 
                   setQosItem("Bitrate", (int) playbackInformation.getBitrate()); 
                   setQosItem("Buffering time", (int) playbackInformation.getBufferingTime());  
                   setQosItem("Buffer length", (int) playbackInformation.getBufferLength());  
                   setQosItem("Buffer time", (int) playbackInformation.getBufferTime());  
                   setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount());  
                   setQosItem("Time to load", (int) playbackInformation.getTimeToLoad());  
                   setQosItem("Time to start", (int) playbackInformation.getTimeToStart()); 
                   setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare()); 
                   setQosItem("Perceived Bandwidth", (int) playbackInformation.getPerceivedBandwidth());   
                   playbackInformation.getPerceivedBandwidth()); 
               } 
           }); 
       }; 
   }; 
   ```

1. (Facultatif) Lisez les informations spécifiques à l’appareil.

   ```java
   // Show device information 
   DeviceInformation deviceInfo = new QOSProvider(parent.getApplicationContext()). 
                                  getDeviceInformation(); 
   tv = (TextView) view.findViewById(R.id.aboutDeviceModel); 
   tv.setText(parent.getString(R.string.aboutDeviceModel) + " " +  
     deviceInfo.getManufacturer() + " - " + deviceInfo.getModel()); 
   
   tv = (TextView) view.findViewById(R.id.aboutDeviceSoftware); 
   tv.setText(parent.getString(R.string.aboutDeviceSoftware) + " " +  
     deviceInfo.getOS() + ", SDK: " + deviceInfo.getSDK()); 
   
   tv = (TextView) view.findViewById(R.id.aboutDeviceResolutin); 
   String orientation = parent.getResources().getConfiguration().orientation ==  
     Configuration.ORIENTATION_LANDSCAPE ? "landscape" : "portrait"; 
   tv.setText(parent.getString(R.string.aboutDeviceResolution) + " " +  
     deviceInfo.getWidthPixels() + "x" + deviceInfo.getHeightPixels() +  
     " (" + orientation + ")"); 
   ```
