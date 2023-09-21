---
description: Le code client transmet des données à une API Android.
title: Processus de demande de clé sur le PSDK Android
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Processus de demande de clé sur le PSDK Android{#key-request-workflow-on-android-psdk}

Le code client transmet des données à une API Android.

Sous Android, votre code client doit transmettre l’URL du serveur de licences et les données d’acquisition de licences associées à l’aide de l’API suivante :

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

Une fois l’appel de cette API réussi, votre code peut alors démarrer la lecture du contenu de la manière habituelle. Si vous utilisez Expressplay, vous pouvez transmettre le jeton dans le cadre de l’URL du serveur de licences ou en tant que propriété de demande et retirer le jeton de l’URL du serveur de licences.

Certains appareils Android prennent en charge Windows et PlayReady. Sur ces périphériques, le client peut vouloir forcer PSDK à déchiffrer le contenu à l’aide d’un DRM spécifique si le contenu comporte plusieurs en-têtes DRM. Pour ce faire, appelez l’API suivante avant la lecture :

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
