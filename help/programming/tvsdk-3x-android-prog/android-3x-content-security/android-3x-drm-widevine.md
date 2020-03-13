---
description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour assurer un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution intégrée d’Adobe.
seo-description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour assurer un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution intégrée d’Adobe.
seo-title: DRM Widevine
title: DRM Widevine
uuid: 3a5fd786-4319-4e92-83b6-0f5328df6a44
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# DRM Widevine {#widevine-drm}

Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour assurer un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution intégrée d’Adobe.

Contactez votre représentant Adobe pour obtenir les informations les plus récentes sur la disponibilité de solutions DRM tierces.

<!--<a id="section_1385440013EF4A9AA45B6AC98919E662"></a>-->

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
