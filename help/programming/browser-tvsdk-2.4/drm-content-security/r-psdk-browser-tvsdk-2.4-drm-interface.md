---
description: Le navigateur TVSDK fournit une interface DRM que vous pouvez utiliser pour lire le contenu protégé par différentes solutions DRM, notamment FairPlay, PlayReady et Widevine.
seo-description: Le navigateur TVSDK fournit une interface DRM que vous pouvez utiliser pour lire le contenu protégé par différentes solutions DRM, notamment FairPlay, PlayReady et Widevine.
seo-title: Présentation de l’interface DRM
title: Présentation de l’interface DRM
uuid: b553ebad-8310-4517-8d97-ef8a1c5f4340
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Présentation de l’interface DRM{#drm-interface-overview}

Le navigateur TVSDK fournit une interface DRM que vous pouvez utiliser pour lire le contenu protégé par différentes solutions DRM, notamment FairPlay, PlayReady et Widevine.

<!--<a id="section_59994F2059B245E996E0776214804A0A"></a>-->

>[!IMPORTANT]
>
>La prise en charge DRM est disponible pour les flux MPEG-Dash protégés par Microsoft PlayReady (sur Internet Explorer sous Windows 8.1 et Edge) et les systèmes DRM Widevine (sur Google Chrome). La prise en charge DRM est disponible pour les flux HLS sur Safari qui sont protégés par FairPlay.

L’interface clé du processus DRM est la `DRMManager`. Une référence à l’ `DRMManager` instance peut être obtenue via l’instance MediaPlayer :

* `var mediaPlayer = new AdobePSDK.MediaPlayer();`
* `var drmManager = mediaPlayer.drmManager;`

<!--<a id="section_B7E8AD9A4D4F4BD9BA2A67ABC135D6F9"></a>-->

Voici un flux de travail de haut niveau pour la lecture de contenu protégé par DRM :

1. Pour joindre les données spécifiques au système DRM qui seront utilisées par le navigateur TVSDK dans le processus d’acquisition de licence d’un flux protégé, effectuez l’appel suivant avant d’appeler `mediaPlayer.replaceCurrentResource`:

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

1. Si le même contenu doit fonctionner avec différents systèmes DRM dans différents navigateurs, les données de protection peuvent être spécifiées pour plusieurs systèmes DRM.

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

1. Lorsque les données de protection ne sont pas définies, les informations nécessaires, telles que l’URL de la licence, sont récupérées dans la zone PSSH pour les systèmes DRM, le cas échéant.

   >[!TIP]
   >
   >La spécification des données de protection remplace l’URL de licence spécifiée dans la zone PSSH.

1. Par défaut, le type de session de la licence DRM est temporaire, ce qui signifie que la licence n’est pas stockée une fois la session fermée.

   Vous pouvez spécifier un type de session à l’aide d’une API dans `DRMManager`.  Pour une compatibilité descendante, les types de session incluent `temporary`, `persistent-license`, `persistent-usage-record`et `persistent`.

   ```js
   var drmManager = mediaPlayer.drmManager; 
    drmManager.setEMESessionType(“<YOUR_SESSION_TYPE>”); 
   ```

1. Lorsque la licence `sessionType` utilisée est `persistent-license` ou `persistent`, la licence DRM peut être renvoyée en appelant `DRMManager.returnLicense`.

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

