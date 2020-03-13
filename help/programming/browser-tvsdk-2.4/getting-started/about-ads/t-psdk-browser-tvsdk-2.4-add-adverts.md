---
description: 'null'
seo-description: 'null'
seo-title: Publicité Ajouter
title: Publicité Ajouter
uuid: 7762506f-b55e-445d-b8a2-c1208358a370
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Publicité Ajouter {#add-advertising}

1. Définissez les métadonnées publicitaires.

   ```js
   var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
     auditudeSettings.domain = "auditude.com"; 
     auditudeSettings.mediaId = "adbe_tearsofsteel2"; 
     auditudeSettings.zoneId = "123869";
   ```

1. Ajouter les métadonnées publicitaires au `MediaResource`.

   ```js
   var mediaResource =  
     new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
   ```

1. Ajouter les paramètres dans la configuration et ajoutez une fabrique `SpliceOut` d’analyseurs.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings; 
   config.advertisingFactory = new ExtCueOutContentFactory(auditudeSettings);
   ```

1. Ajouter la section `ExtCueOutContentFactory` à la bibliothèque.
1. Téléchargez la `ExtCueOutContentFactory.js` section de la bibliothèque et placez-la dans le dossier de travail.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script> 
   <script src= "ExtCueOutContentFactory.js"></script>
   ```

1. Testez votre configuration.
