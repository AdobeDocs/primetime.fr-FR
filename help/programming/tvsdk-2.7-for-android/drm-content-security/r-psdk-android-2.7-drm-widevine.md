---
description: Vous pouvez utiliser le DRM Android natif de Widevine avec les flux DASH.
title: DRM sans fil
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---


# DRM sans fil {#widevine-drm}

Vous pouvez utiliser le DRM Android natif de Widevine avec les flux DASH.

Appelez l&#39;API `com.adobe.mediacore.drm.DRMManager` suivante avant de commencer la lecture :

```java
public static void setProtectionData( 
    String drm,  
    String licenseServerURL,   
    Map<String, String> requestProperties)
```

Arguments :

* `drm` -  `"com.widevine.alpha"` pour Widevine.

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

