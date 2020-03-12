---
description: Vous pouvez exécuter des  spécifiques à Digital Rights Management (DRM).
seo-description: Vous pouvez exécuter des  spécifiques à Digital Rights Management (DRM).
seo-title: Gestion des droits numériques
title: Gestion des droits numériques
uuid: 011605c7-50c4-4ad5-9961-8cd92d0e6fd8
translation-type: tm+mt
source-git-commit: 5a786d8001326f874a51d65b8e8badca44f46e96

---


# Gestion des droits numériques {#digital-rights-management}

Vous pouvez exécuter des  spécifiques à Digital Rights Management (DRM).

Vous pouvez écouter le `AdobePSDK.DRMMetadataInfoEvent` pour gérer le DRM  :

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvailable);
...
```

## Ajouter Gestion des droits numériques {#add-digital-rights-management}

1. Ajouter le `DRMMetadataInfoAvailableEvent` pour obtenir le `DRMMetadata`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvaialble);
   ```

1. Mettez en oeuvre la `onDRMMetadataInfoAvailable` section au-dessus de la ligne de l’étape 1.

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

1. Ajouter les données de protection au gestionnaire de fichiers drmManager.

   ```js
   drmManager.setProtectionData(protectionData);
   ```

1. Modifiez l’URL de la ressource en un flux de test DASH.

   >[!TIP]
   >
   >Veillez à mettre à jour le type de ressource, car il s’agit maintenant de DASH.

   ```js
   var resourceUrl = "https://ptdemos.com/videos/dashdrm/stream.mpd"; 
   var resourceType = AdobePSDK.MediaResourceType.DASH;
   ```

1. Testez votre configuration.