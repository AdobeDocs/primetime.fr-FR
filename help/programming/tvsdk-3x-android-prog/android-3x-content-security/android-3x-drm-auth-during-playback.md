---
description: Lorsque les métadonnées DRM d’une vidéo sont incluses dans le flux multimédia, vous pouvez effectuer une authentification pendant la lecture.
title: Authentification DRM pendant la lecture
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Authentification DRM pendant la lecture {#drm-authentication-during-playback}

Lorsque les métadonnées DRM d’une vidéo sont incluses dans le flux multimédia, vous pouvez effectuer une authentification pendant la lecture.

Avec la rotation des licences, une ressource est chiffrée avec plusieurs licences DRM. Chaque fois que de nouvelles métadonnées DRM sont découvertes, la variable `DRMHelper` sont utilisées pour vérifier si les métadonnées DRM nécessitent une authentification DRM.

>[!TIP]
>
>Avant de commencer la lecture, déterminez si vous avez affaire à une licence liée à un domaine et si l’authentification de domaine est requise. Si oui, effectuez l’authentification de domaine et rejoignez le domaine.

1. Lorsque de nouvelles métadonnées DRM sont découvertes dans une ressource, un événement est distribué au niveau de la couche de l’application.

   ```java
   mediaPlayer.addEventListener(MediaPlayerEvent.DRM_METADATA,  
                                drmMetadataInfoEventListener); 
   
   DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
     new DRMMetadataInfoEventListener() { 
       @Override 
       public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
           ... 
       } 
   };
   ```

1. Utilisez la variable `DRMMetadata` pour vérifier si l’authentification est nécessaire.

   * Si l’authentification n’est pas requise, vous n’avez rien à faire et la lecture se poursuit sans interruption.
   * Si l’authentification est requise, effectuez l’authentification DRM.

     Cette opération étant asynchrone et gérée dans un autre thread, elle n’a aucun impact sur l’interface utilisateur ni sur la lecture vidéo.

1. Si l’authentification échoue, l’utilisateur ne peut pas continuer à regarder la vidéo et la lecture s’arrête.

<!--<a id="example_939B95F831A245869F9248E2767F260C"></a>-->

Par exemple :

```java
DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
  new DRMMetadataInfoEventListener() { 
    @Override 
    public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
        final DRMMetadataInfo drmMetadataInfo =  
          drmMetadataInfoEvent.getDRMMetadataInfo(); 
 
        if (drmMetadataInfo == null ||  
          !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { 
            return; 
        } 
 
        // Perform DRM auth. 
        // Possible logic might take into consideration a threshold between the  
        // current player time and the DRM metadata start time. For the time being,  
        // we resolve it as soon as we receive the DRM metadata. 
 
        DRMManager drmManager = _mediaPlayer.getDRMManager(); 
        if (drmManager == null) { 
            return; 
        } 
 
        SharedPreferences sharedPreferences =  
          PreferenceManager.getDefaultSharedPreferences(getActivity()); 
        String authUser = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_USERNAME,  
          getResources().getString(R.string.drmUsername)); 
        String authPass = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_PASSWORD,  
          getResources().getString(R.string.drmPassword)); 
 
        DRMHelper.performDrmAuthentication(drmManager, drmMetadataInfo.getDRMMetadata(),  
          authUser, authPass, new DRMAuthenticationListener() { 
 
            @Override 
            public void onAuthenticationStart() { 
                ... 
            } 
 
            @Override 
            public void onAuthenticationError(int major,  
                                              int minor,  
                                              String erroString,  
                                              String serverErrorURL) { 
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
