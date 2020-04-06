---
description: Lorsque les métadonnées DRM d’une vidéo sont distinctes du flux média, vous devez vous authentifier avant de commencer la lecture.
seo-description: Lorsque les métadonnées DRM d’une vidéo sont distinctes du flux média, vous devez vous authentifier avant de commencer la lecture.
seo-title: Authentification DRM avant lecture
title: Authentification DRM avant lecture
uuid: be319b04-a506-4278-8275-db32cd3f18aa
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Authentification DRM avant lecture {#drm-authentication-before-playback}

Lorsque les métadonnées DRM d’une vidéo sont distinctes du flux média, vous devez vous authentifier avant de commencer la lecture.

Un fichier vidéo peut être associé à un fichier de métadonnées DRM, par exemple :

* `"url": "https://www.domain.com/asset.m3u8"`
* `"drmMetadata": "https://www.domain.com/asset.metadata"`

Dans cet exemple, vous pouvez utiliser `DRMHelper` des méthodes pour télécharger le contenu du fichier de métadonnées DRM, l’analyser et vérifier si l’authentification DRM est nécessaire.

1. Utilisez `loadDRMMetadata` pour charger le contenu de l’URL de métadonnées et analyser les octets téléchargés en un `DRMMetadata`.

   >[!TIP]
   >
   >Cette méthode est asynchrone et crée son propre thread.

   ```java
   public static void loadDRMMetadata( 
       final DRMManager drmManager, 
       final String drmMetadataUrl,  
       final DRMLoadMetadataListener loadMetadataListener); 
   ```

   Par exemple :

   ```java
   DRMHelper.loadDRMMetadata(drmManager,  
                                      metadataURL,  
                                      new DRMLoadMetadataListener());
   ```

1. Avertissez l’utilisateur que cette opération est asynchrone. Il est conseillé de le signaler à l’utilisateur.

   Si les utilisateurs ne savent pas que l’opération est asynchrone, ils peuvent se demander pourquoi la lecture n’a pas encore commencé. Vous pouvez, par exemple, afficher une roue dentée pendant le téléchargement et l’analyse des métadonnées DRM.

1. Implémentez les rappels dans le `DRMLoadMetadataListener`.

   Le paramètre &quot;loadDRMMetadata&quot; appelle ces gestionnaires de de.

   ```java    
   public interface DRMLoadMetadataListener { 
    
       public void onLoadMetadataUrlStart(); 
    
       /** 
       * @param authNeeded 
       * whether DRM authentication is needed. 
       * @param drmMetadata 
       * the parsed DRMMetadata obtained.    */ 
       public void onLoadMetadataUrlComplete(boolean authNeeded, DRMMetadata drmMetadata); 
       public void onLoadMetadataUrlError(); 
   } 
   
   ```

   Voici des informations supplémentaires sur les gestionnaires :

   * `onLoadMetadataUrlStart` détecte le début du chargement de l’URL de métadonnées.
   * `onLoadMetadataUrlComplete` détecte la fin du chargement de l’URL de métadonnées.
   * `onLoadMetadataUrlError` indique que le chargement des métadonnées a échoué.

1. Une fois le chargement terminé, examinez l’ `DRMMetadata` objet pour déterminer si l’authentification DRM est requise.

   ```java
   public static boolean isAuthNeeded(DRMMetadata drmMetadata);
   ```

   Par exemple :

   ```java
   @Override 
   public void onLoadMetadataUrlComplete(boolean authNeeded, DRMMetadata drmMetadata) {  
       Log.i(LOG_TAG + "#onLoadMetadataUrlComplete",  
             "Loaded metadata URL contents. Auth needed:" + authNeeded + "."); 
       if (!authNeeded) { 
           // Auth is not required. Start player activity.     
           showLoadingSpinner(false);     
           startPlayerActivity(ASSET_URL); 
           return; 
       } 
   } 
   ```

1. Renseignez l’un des  suivants :

   * Si l’authentification n’est pas requise, commencez la lecture.
   * Si l’authentification est requise, effectuez l’authentification en acquérant la licence.

      ```java
      /** 
      * Helper method to perform DRM authentication. 
      * 
      * @param drmManager 
      * the DRMManager, used to perform the authentication. 
      * @param drmMetadata 
      * the DRMMetadata, containing the DRM specific information. 
      * @param authenticationListener 
      * the listener, on which the user can be notified about the 
      * authentication process status. 
      */ 
      public static void performDrmAuthentication( 
           final DRMManager drmManager,  
           final DRMMetadata drmMetadata, 
           final String authUser,  
           final String authPass,  
           final DRMAuthenticationListener authenticationListener);
      ```

      Dans cet exemple, pour simplifier, le nom et le mot de passe de l’utilisateur sont codés explicitement :

      ```java
      DRMHelper.performDrmAuthentication(drmManager,  
                                         drmMetadata,  
                                         DRM_USERNAME,  
                                         DRM_PASSWORD, new DRMAuthenticationListener() { 
          @Override 
          public void onAuthenticationStart() { 
              Log.i(LOG_TAG + "#onAuthenticationStart", "DRM authentication started."); 
              // Spinner is already showing. 
          } 
          @Override 
          public void onAuthenticationError(int major,  
                                            int minor,  
                                            String errorString,  
                                            String serverErrorURL) { 
              Log.e(LOG_TAG +  
                    "#onAuthenticationError",  
                    "DRM authentication failed. " +  
                    major + " 0x" + Long.toHexString(minor)); 
              showToast(getString(R.string.drmAuthenticationError));   
              showLoadingSpinner(false); 
          } 
          @Override 
          public void onAuthenticationComplete(byte[] authenticationToken) { 
              Log.i(LOG_TAG +  
                    "#onAuthenticationComplete", "Auth successful. Launching content."); 
              showLoadingSpinner(false); 
              startPlayerActivity(ASSET_URL); 
          } 
      }); 
      ```

1. Utilisez un écouteur  pour vérifier l’état de l’authentification.

   Ce processus implique une communication réseau. Il s’agit donc également d’une opération asynchrone.

   ```java
   public interface DRMAuthenticationListener { 
       /** 
       * Called to indicate that DRM authentication has started. 
       */ 
       public void onAuthenticationStart(); 
       /** 
       * Called to indicate that DRM authentication has been successful. 
       * 
       * @param authenticationToken 
       * the obtained token, which can be stored locally. 
       */ 
       public void onAuthenticationComplete(byte[] authenticationToken); 
       /** 
       * Called to indicate that an error occurred while performing the DRM 
       * authentication. 
       * 
       * @param major 
       * the major code. 
       * @param minorC 
       * the minor code. 
       * @param errorString 
       * the exception thrown. 
       * @param serverErrorURL 
       * the URL of the server  
       * on which the error occurred 
       */ 
       public void onAuthenticationError(int major,  
                                         int minor,  
                                         String errorString,  
                                         String serverErrorURL); 
   } 
   ```

1. Si l’authentification réussit, la lecture.
1. Si l’authentification échoue, avertissez l’utilisateur et n’pas la lecture .

   Votre application doit gérer toutes les erreurs d’authentification. Echec de l’authentification avant la lecture place TVSDK dans un état d’erreur et la lecture s’arrête. Votre application doit résoudre le problème, réinitialiser le lecteur et recharger la ressource.
