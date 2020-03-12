---
description: Vous pouvez utiliser le DRM Android natif Widevine avec les flux DASH.
seo-description: Vous pouvez utiliser le DRM Android natif Widevine avec les flux DASH.
seo-title: DRM Widevine
title: DRM Widevine
uuid: ceb2f18f-9e53-47d6-9d4b-7004ac1d22c9
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# DRM Widevine {#widevine-drm}

Vous pouvez utiliser le DRM Android natif Widevine avec les flux DASH.

Appelez l’ `com.adobe.mediacore.drm.DRMManager` API suivante avant de commencer la lecture :

```java
public static void setProtectionData( 
    String drm,  
    String licenseServerURL,   
    Map<String, String> requestProperties)
```

Arguments :

* `drm` - `"com.widevine.alpha"` pour Widevine.

* `licenseServerURL` - URL du serveur de licences Widevine qui reçoit les demandes de licence.
* `requestProperties` - Contient des en-têtes supplémentaires à inclure dans la demande de licence sortante.

Par exemple, lors de l’utilisation de contenu compressé pour Expressplay DRM, utilisez le code suivant avant de lire :

```java
DRMManager.setProtectionData( 
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null); 
```

