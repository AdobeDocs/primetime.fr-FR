---
description: Vous pouvez utiliser Android native Widevine DRM avec les flux DASH.
title: Widevine DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---

# Widevine DRM {#widevine-drm}

Vous pouvez utiliser Android native Widevine DRM avec les flux DASH.

Appelez ce qui suit `com.adobe.mediacore.drm.DRMManager` API avant de commencer la lecture :

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

Par exemple, lors de l’utilisation de contenu mis en package pour Expressplay DRM, utilisez le code suivant avant la lecture :

```java
DRMManager.setProtectionData( 
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null); 
```
