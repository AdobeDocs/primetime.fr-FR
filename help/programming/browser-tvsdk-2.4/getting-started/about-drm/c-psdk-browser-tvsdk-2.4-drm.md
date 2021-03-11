---
description: Vous pouvez exécuter des workflows spécifiques à un Digital Rights Management (DRM).
title: Digital Rights Management
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Digital Rights Management {#digital-rights-management}

Vous pouvez exécuter des workflows spécifiques à un Digital Rights Management (DRM).

Vous pouvez écouter le événement `AdobePSDK.DRMMetadataInfoEvent` pour gérer les workflows DRM :

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvailable);
...
```

## Digital Rights Management d&#39;Ajoute {#add-digital-rights-management}

1. Ajoutez `DRMMetadataInfoAvailableEvent` pour obtenir `DRMMetadata`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvaialble);
   ```

1. Mettez en oeuvre la section `onDRMMetadataInfoAvailable` au-dessus de la ligne de l’étape 1.

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

1. Créez DRMManager dans la méthode setupVideo.

   ```js
   var drmManager = player.drmManager;
   ```

1. Créez les données de protection pour Windows et PlayReady en copiant l’exemple suivant :

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

1. Modifiez l’URL de la ressource en un flux de test DASH.

   >[!TIP]
   >
   >Assurez-vous de mettre à jour le type de ressource, car il s’agit maintenant de DASH.

   ```js
   var resourceUrl = "https://ptdemos.com/videos/dashdrm/stream.mpd"; 
   var resourceType = AdobePSDK.MediaResourceType.DASH;
   ```

1. Testez votre configuration.