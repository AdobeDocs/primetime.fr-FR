---
description: Lorsque les métadonnées DRM d’une vidéo sont incluses dans le flux média, effectuez l’authentification pendant la lecture.
seo-description: Lorsque les métadonnées DRM d’une vidéo sont incluses dans le flux média, effectuez l’authentification pendant la lecture.
seo-title: Authentification DRM pendant la lecture
title: Authentification DRM pendant la lecture
uuid: a1a63e3e-be34-49e1-96c4-ae266003b3d1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Authentification DRM pendant la lecture {#drm-authentication-during-playback}

Lorsque les métadonnées DRM d’une vidéo sont incluses dans le flux média, effectuez l’authentification pendant la lecture.

Prenons l’exemple de la fonction de rotation des licences, qui consiste à chiffrer un fichier avec plusieurs licences DRM. Chaque fois que de nouvelles métadonnées DRM sont découvertes, utilisez les méthodes `DRMHelper` pour vérifier si les métadonnées DRM nécessitent une authentification DRM.

>[!NOTE]
>
>Ce didacticiel ne traite pas les licences liées aux domaines. Idéalement, avant de commencer la lecture, vérifiez si vous utilisez une licence liée au domaine. Si oui, effectuez l’authentification de domaine (si nécessaire) et joignez le domaine.

1. Lorsque de nouvelles métadonnées DRM sont découvertes dans une ressource, un événement est distribué dans la couche de l’application.

   ```java
   mediaPlayer.addEventListener(MediaPlayerEvent.DRM_METADATA,  
                                drmMetadataInfoEventListener); 
   
   DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
     new DRMMetadataInfoEventListener() { 
           @Override 
           public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
           } 
   };
   ```

1. Utilisez `DRMMetadata` pour vérifier si une authentification est nécessaire. Dans le cas contraire, ne rien faire ; la lecture se poursuit sans interruption.
1. Sinon, effectuez l’authentification DRM. Cette opération étant asynchrone et gérée dans un thread différent, elle n’a aucun impact sur l’interface utilisateur ni sur la lecture vidéo.
1. Si l’authentification échoue, l’utilisateur ne peut pas continuer à regarder la vidéo et la lecture cesse. Sinon, la lecture se poursuit sans interruption.

```java
DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
  new DRMMetadataInfoEventListener() { 
    @Override 
    public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
        final DRMMetadataInfo drmMetadataInfo = drmMetadataInfoEvent.getDRMMetadataInfo(); 
 
        if (drmMetadataInfo == null || !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { 
            return; 
        } 
 
        // Perform DRM auth. 
        // Possible logic might take into consideration a threshold between the current player time and the 
        // DRM metadata start time. For the time being, we resolve it as soon as we receive the DRM metadata. 
 
        DRMManager drmManager = _mediaPlayer.getDRMManager(); 
        if (drmManager == null) { 
            return; 
        } 
 
        SharedPreferences sharedPreferences = PreferenceManager.getDefaultSharedPreferences(getActivity()); 
        String authUser = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_USERNAME,  
          getResources().getString(R.string.drmUsername)); 
          String authPass = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_PASSWORD,  
          getResources().getString(R.string.drmPassword)); 
 
        DRMHelper.performDrmAuthentication(drmManager, drmMetadataInfo.getDRMMetadata(),  
          authUser, authPass, new DRMAuthenticationListener() { 
 
            @Override 
            public void onAuthenticationStart() { 
            } 
 
            @Override 
            public void onAuthenticationError(int major, int minor, String erroString, String serverErrorURL) { 
                if (getActivity() == null) { 
                    return; 
                } 
                _handler.post(new Runnable() { 
                    @Override 
                    public void run() { 
                        showToast(getString(R.string.drmAuthenticationError)); 
                        getActivity().finish(); 
                    } 
                }); 
            } 
 
            @Override 
            public void onAuthenticationComplete(byte[] authenticationToken) { 
            } 
        }); 
    } 
};
```
