---
description: Le navigateur TVSDK fournit une interface DRM que vous pouvez utiliser pour lire du contenu protégé par différentes solutions DRM, y compris FairPlay, PlayReady et Widevine.
title: Présentation de l’interface DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Présentation de l’interface DRM{#drm-interface-overview}

Le navigateur TVSDK fournit une interface DRM que vous pouvez utiliser pour lire du contenu protégé par différentes solutions DRM, y compris FairPlay, PlayReady et Widevine.

<!--<a id="section_59994F2059B245E996E0776214804A0A"></a>-->

>[!IMPORTANT]
>
>La prise en charge de DRM est disponible pour les flux MPEG-Dash protégés par Microsoft PlayReady (sur Internet Explorer sous Windows 8.1 et Edge) et les systèmes DRM Windows (sur Google Chrome). La prise en charge de DRM est disponible pour les flux HLS sur Safari protégés par FairPlay.

L’interface clé du processus DRM est la suivante : `DRMManager`. Une référence au `DRMManager` Vous pouvez obtenir l’instance via l’instance MediaPlayer :

* `var mediaPlayer = new AdobePSDK.MediaPlayer();`
* `var drmManager = mediaPlayer.drmManager;`

<!--<a id="section_B7E8AD9A4D4F4BD9BA2A67ABC135D6F9"></a>-->

Voici un workflow de haut niveau pour la lecture de contenu protégé par DRM :

1. Pour joindre les données spécifiques au système DRM qui seront utilisées par le SDK du navigateur dans le processus d’acquisition de licences pour un flux protégé, effectuez l’appel suivant avant d’appeler `mediaPlayer.replaceCurrentResource`:

   ```js
   var protectionData = { 
       "com.adobe.primetime": { 
          "serverURL": { 
             "individualization-request": "https://individualization.adobe.com/flashaccess/i15n/v5", 
             "license-request": "https://example.com:8096/flashaccess/req", 
             "license-release": "https://example.com:8096/flashaccess/req" 
          }, 
          "httpRequestHeaders": { 
          } 
       } 
   }; 
   var drmManager = mediaPlayer.drmManager; 
   drmManager.setProtectionData(protectionData);
   ```

1. Si un même contenu doit fonctionner avec différents systèmes DRM dans différents navigateurs, les données de protection peuvent être spécifiées pour plusieurs systèmes DRM.

   ```js
   var protectionData = { 
       "com.adobe.primetime": { 
           "serverURL": { 
               "individualization-request": "https://individualization.adobe.com/flashaccess/i15n/v5", 
               "license-request": "https://example.com:8096/flashaccess/req", 
               "license-release": "https://example.com:8096/flashaccess/req" 
           }, 
           "httpRequestHeaders": { 
           } 
       }, 
       "com.widevine.alpha": { 
           "serverURL": "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<token value>", 
           "httpRequestHeaders": { 
               "dt-custom-data": "eyJ1c2VySWQiOiIxMjM0NS" 
           } 
       }, 
       "com.microsoft.playready": { 
           "serverURL": "https://pr.test.expressplay.com/playready/RightsManager.asmx?ExpressPlayToken=<token value>", 
           "httpRequestHeaders": { 
               "http-header-CustomData": "eyJ1c2VySWQiOiIxMjM0NS" 
           } 
       }, 
       "com.apple.fps.1_0": { 
           "serverURL": "https://fp.service.expressplay.com:80/hms/fp/rights/?ExpressPlayToken=<token value>", 
           "certificateURL": "Path_To_certificate.cer", 
           "licenseResponseType": "arraybuffer", 
           "httpRequestHeaders": { 
               "Content-type": "application/octet-stream" 
           } 
       }, 
       "org.w3.clearkey": { 
           "clearkeys": { 
               "H3JbV93QV3mPNBKQON2UtQ": "ClKhDPHMtCouEx1vLGsJsA", 
               "IAAAACAAIAAgACAAAAAAAg": "5t1CjnbMFURBou087OSj2w" 
           } 
       } 
   }; 
   
   var drmManager = mediaPlayer.drmManager; 
   drmManager.setProtectionData(protectionData);
   ```

1. Lorsque les données de protection ne sont pas définies, les informations nécessaires telles que l’URL de licence sont récupérées dans la zone PSSH pour les systèmes DRM, le cas échéant.

   >[!TIP]
   >
   >La spécification de données de protection remplace l’URL de licence spécifiée dans la zone PSSH.

1. Par défaut, le type de session de la licence DRM est temporaire, ce qui signifie que la licence n’est pas stockée une fois la session fermée.

   Vous pouvez spécifier un type de session à l’aide d’une API dans `DRMManager`.  Pour une compatibilité descendante, les types de session incluent `temporary`, `persistent-license`, `persistent-usage-record`, et `persistent`.

   ```js
   var drmManager = mediaPlayer.drmManager; 
    drmManager.setEMESessionType(“<YOUR_SESSION_TYPE>”); 
   ```

1. Lorsque la variable `sessionType` used is `persistent-license` ou `persistent`, la licence DRM peut être renvoyée en appelant `DRMManager.returnLicense`.

   ```js
   var onLicenseReturnFunc = function () { 
       console.log("DRM: License Return Complete "); 
   }, 
   
   onLicenseReturnErrorFunc = function (major, minor, errorString/*, errorServerUrl*/) { 
      console.log("DRM: License Return Error: " + errorString); 
   }, 
   
   drmManager = mediaPlayer.drmManager; 
   
   if (drmManager) { 
       var returnLicenseListener = new  
           AdobePSDK.DRMReturnLicenseListener(onLicenseReturnFunc, onLicenseReturnErrorFunc); 
       drmManager.returnLicense(null, null, null, false, returnLicenseListener, drmLicense.session); 
   }
   ```
