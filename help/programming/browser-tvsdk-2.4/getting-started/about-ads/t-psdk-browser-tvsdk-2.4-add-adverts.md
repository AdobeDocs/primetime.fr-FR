---
title: Ajouter une publicité
description: Ajouter une publicité
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Ajouter une publicité {#add-advertising}

1. Définissez les métadonnées publicitaires.

   ```js
   var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
     auditudeSettings.domain = "auditude.com"; 
     auditudeSettings.mediaId = "adbe_tearsofsteel2"; 
     auditudeSettings.zoneId = "123869";
   ```

1. Ajoutez les métadonnées publicitaires au `MediaResource`.

   ```js
   var mediaResource =  
     new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
   ```

1. Ajoutez les paramètres à la configuration et ajoutez une `SpliceOut` usine analyseur.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings; 
   config.advertisingFactory = new ExtCueOutContentFactory(auditudeSettings);
   ```

1. Ajoutez la variable `ExtCueOutContentFactory` à la section bibliothèque .
1. Téléchargez la `ExtCueOutContentFactory.js` à partir de la section bibliothèque et placez-la dans le dossier de travail.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script> 
   <script src= "ExtCueOutContentFactory.js"></script>
   ```

1. Testez votre configuration.
