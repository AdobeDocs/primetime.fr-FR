---
description: Le code client transmet les données à une API Android.
title: Processus de demande de clé sur le PSDK Android
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# Processus de demande de clé sur le PSDK Android{#key-request-workflow-on-android-psdk}

Le code client transmet les données à une API Android.

Sous Android, le code client doit transmettre l’URL du serveur de licences et les données d’acquisition de licences associées à l’aide de l’API suivante :

```
class DRMManager 
   { 
   ... 
   /* 
   * Set the license server URL and attached request properties that the PSDK should use for the passed in drm type.  
   * 
   * drmType: "com.widevine.alpha" for widevine. "com.microsoft.playready" for playready. 
   * licenseServerURL: self explanatory.  
   * requestProperties: key value pairs to be attached as HTTP headers to all license request sent to the passed in license server URL. Pass in 
   * NULL if none is needed.  
   */ 
   public static void setProtectionData(String drmType, String licenseServerURL,  Map<String, String> requestProperties); 
    }
```

Après avoir appelé cette API, votre code peut alors début la lecture du contenu de la manière habituelle. Si vous utilisez Expressplay, vous pouvez transmettre le jeton dans le cadre de l’URL du serveur de licences ou en tant que propriété de requête et le retirer de l’URL du serveur de licences.

Certains périphériques Android prennent en charge Widevine et PlayReady. Sur ces périphériques, le client peut vouloir forcer PSDK à déchiffrer le contenu à l’aide d’un DRM particulier si le contenu comporte plusieurs en-têtes DRM. Pour ce faire, appelez l’API suivante avant de lire :

```
class MediaPlayer 
   { 
   ... 
    
   /* 
   * drm: pass in "com.widevine.alpha" for widevine or "com.microsoft.playready" for playready 
   * 
   */ 
   public void setDRMScheme(String drm) throws MediaPlayerException 
   }
```

