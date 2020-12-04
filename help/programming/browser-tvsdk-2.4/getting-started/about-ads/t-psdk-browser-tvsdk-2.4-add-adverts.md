---
description: 'null'
seo-description: 'null'
seo-title: Ajouter la publicité
title: Ajouter la publicité
uuid: 7762506f-b55e-445d-b8a2-c1208358a370
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '51'
ht-degree: 0%

---


# Publicité d&#39;Ajoute {#add-advertising}

1. Définissez les métadonnées publicitaires.

   ```js
   var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
     auditudeSettings.domain = "auditude.com"; 
     auditudeSettings.mediaId = "adbe_tearsofsteel2"; 
     auditudeSettings.zoneId = "123869";
   ```

1. Ajoutez les métadonnées publicitaires sur `MediaResource`.

   ```js
   var mediaResource =  
     new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
   ```

1. Ajoutez les paramètres dans la configuration et ajoutez une fabrique d&#39;analyseurs `SpliceOut`.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings; 
   config.advertisingFactory = new ExtCueOutContentFactory(auditudeSettings);
   ```

1. Ajoutez `ExtCueOutContentFactory` dans la section de bibliothèque.
1. Téléchargez le `ExtCueOutContentFactory.js` à partir de la section de bibliothèque et placez-le dans le dossier de travail.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script> 
   <script src= "ExtCueOutContentFactory.js"></script>
   ```

1. Testez votre configuration.
