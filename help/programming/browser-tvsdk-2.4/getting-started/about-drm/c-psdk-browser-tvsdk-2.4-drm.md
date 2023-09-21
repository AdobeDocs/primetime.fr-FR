---
description: Vous pouvez exécuter des workflows spécifiques à un Digital Rights Management (DRM).
title: Digital Rights Management
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Digital Rights Management {#digital-rights-management}

Vous pouvez exécuter des workflows spécifiques à un Digital Rights Management (DRM).

Vous pouvez écouter le `AdobePSDK.DRMMetadataInfoEvent` pour gérer les workflows DRM :

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvailable);
...
```

## Ajouter un Digital Rights Management {#add-digital-rights-management}

1. Ajoutez la variable `DRMMetadataInfoAvailableEvent` pour obtenir le `DRMMetadata`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvaialble);
   ```

1. Mettez en oeuvre le `onDRMMetadataInfoAvailable` au-dessus de la ligne de l’étape 1.

   ```js
   var onDRMMetadataInfoAvaialble = function(event) { 
    var drmMetadataInfo = event.drmMetadataInfo; 
    var drmMetadata = null; 
   
    if(drmMetadataInfo) { 
     drmMetadata = drmMetadataInfo.drmMetadata; 
    } 
   
    drmManager.acquireLicense(drmMetadata, null, null); 
   };
   ```

1. Créez le DRMManager dans la méthode setupVideo .

   ```js
   var drmManager = player.drmManager;
   ```

1. Créez les données de protection pour Widevine et PlayReady en copiant l’exemple suivant :

   ```js
   var protectionData = { 
     "com.widevine.alpha":{ 
       "serverURL":"https://wv.service.expressplay.com/hms/wv/rights/? 
                    ExpressPlayToken=[YOUR_EXPRESSPLAY_TOKEN]"  
     }, 
   
     "com.microsoft.playready":{ 
       "serverURL":"https://pr.test.expressplay.com/playready/RightsManager.asmx? 
                    ExpressPlayToken=[YOUR_EXPRESSPLAY_TOKEN]", 
         "httpRequestHeaders":{ 
       } 
     } 
   };
   ```

1. Ajoutez les données de protection à drmManager.

   ```js
   drmManager.setProtectionData(protectionData);
   ```

1. Remplacez l’URL de la ressource par un flux de test DASH.

   >[!TIP]
   >
   >Veillez à mettre à jour le type de ressource, car il s’agit désormais de DASH.

   ```js
   var resourceUrl = "https://ptdemos.com/videos/dashdrm/stream.mpd"; 
   var resourceType = AdobePSDK.MediaResourceType.DASH;
   ```

1. Testez votre configuration.
