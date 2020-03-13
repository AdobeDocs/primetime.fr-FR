---
description: La qualité du service (QoS) fournit un détaillé sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
seo-description: La qualité du service (QoS) fournit un détaillé sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
seo-title: Statistiques sur la qualité du service
title: Statistiques sur la qualité du service
uuid: 3d66ed44-9d4a-4162-962f-e238575ff2dd
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Statistiques sur la qualité du service {#quality-of-service-statistics}

La qualité du service (QoS) fournit un détaillé sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.

TVSDK fournit également des informations sur les ressources téléchargées suivantes :

* Fichiers de liste de lecture/manifestes
* Fragments de fichier
* Informations de suivi des fichiers

## Suivi au niveau du fragment à l’aide des informations de chargement {#section_4439D91E8EDC45588EF1D7BE25697350}

Vous pouvez lire des informations sur la qualité du service (QoS) à propos des ressources téléchargées, telles que des fragments et des pistes, à partir de la `LoadInformation` classe.

1. Mettez en oeuvre et enregistrez le `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` module d’écoute .
1. Appelez `event.getLoadInformation()` pour lire les données pertinentes du `event` paramètre transmis au rappel.

   >[!NOTE]
   >
   >Pour plus d’informations `LoadInformation`, voir [3.0 pour les documents API Android (Java)](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.0/index.html) .

## Lecture des statistiques de lecture, de mise en mémoire tampon et de périphérique QOS {#section_D21722600F324E67A9F06234D338B243}

Vous pouvez lire les statistiques de lecture, de mise en mémoire tampon et de périphérique à partir de la `QOSProvider` classe.

La `QOSProvider` classe fournit diverses statistiques, notamment des informations sur la mise en mémoire tampon, les débits, les débits d’images, les données temporelles, etc. Il fournit également des informations sur le périphérique, telles que le fabricant, le modèle, le système d’exploitation, la version du SDK, l’ID du périphérique du fabricant et la taille/densité d’écran.

1. Instanciez un lecteur multimédia.
1. Créez un `QOSProvider` objet et joignez-le au lecteur de médias.

   Le `QOSProvider` constructeur prend un contexte de lecteur afin de pouvoir récupérer des informations spécifiques au périphérique.

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Facultatif) Lisez les statistiques de lecture.

   Une solution pour lire les statistiques de lecture consiste à disposer d’un minuteur, qui récupère régulièrement les nouvelles valeurs de la qualité de service `QOSProvider`.

   Par exemple :

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

1. (Facultatif) Lisez les informations spécifiques au périphérique.

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
