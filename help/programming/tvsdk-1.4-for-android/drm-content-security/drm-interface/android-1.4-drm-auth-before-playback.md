---
description: Lorsque les métadonnées DRM d’une vidéo sont distinctes du flux média, effectuez l’authentification avant de commencer la lecture.
title: Authentification DRM avant lecture
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---


# Authentification DRM avant lecture {#drm-authentication-before-playback}

Lorsque les métadonnées DRM d’une vidéo sont distinctes du flux média, effectuez l’authentification avant de commencer la lecture.

Un fichier vidéo peut être associé à un fichier de métadonnées DRM. Par exemple :

* &quot;url&quot; : &quot;ht<span></span>tps://www.domain.com/asset.m3u8&quot;
* &quot;drmMetadata&quot; : &quot;ht<span></span>tps://www.domain.com/asset.metadata&quot;

Dans ce cas, utilisez les méthodes `DRMHelper` pour télécharger le contenu du fichier de métadonnées DRM, l’analyser et vérifier si l’authentification DRM est nécessaire.

1. Utilisez `loadDRMMetadata` pour charger le contenu de l’URL de métadonnées et analyser les octets téléchargés dans `DRMMetadata`.

   Comme toute autre opération réseau, cette méthode est asynchrone, créant ainsi son propre thread.

   ```java
   public static void loadDRMMetadata( 
       final DRMManager drmManager, 
       final String drmMetadataUrl,  
       final DRMLoadMetadataListener loadMetadataListener); 
   ```

   Par exemple :

   ```java
   DRMHelper.loadDRMMetadata(drmManager, metadataURL, new DRMLoadMetadataListener());
   ```

1. L’opération étant asynchrone, il est conseillé de sensibiliser l’utilisateur à ce problème. Sinon, il se demandera pourquoi sa lecture ne commence pas. Par exemple, affichez une roue dentée pendant que les métadonnées DRM sont téléchargées et analysées.
1. Mettez en oeuvre les rappels dans `DRMLoadMetadataListener`. `loadDRMMetadata` appelle ces gestionnaires de événement (distribue ces événements).

   ```java
   public interface  
    <b>DRMLoadMetadataListener</b> { 
    public void  
    <b>onLoadMetadataUrlStart</b>(); 
    /** 
     * @param authNeeded 
     * whether DRM authentication is needed. 
     * @param drmMetadata 
     * the parsed DRMMetadata obtained.    */ 
    public void  
    <b>onLoadMetadataUrlComplete</b>(boolean authNeeded, DRMMetadata drmMetadata); 
    public void  
    <b>onLoadMetadataUrlError</b>(); 
   }
   ```

   * `onLoadMetadataUrlStart` détecte le début du chargement de l’URL de métadonnées.
   * `onLoadMetadataUrlComplete` détecte la fin du chargement de l’URL de métadonnées.
   * `onLoadMetadataUrlError` indique que le chargement des métadonnées a échoué.

1. Une fois le chargement terminé, inspectez l&#39;objet `DRMMetadata` pour vérifier si l&#39;authentification DRM est nécessaire.

   ```java
   public static boolean <b>isAuthNeeded</b>(DRMMetadata drmMetadata);
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
   ```

1. Si l’authentification n’est pas nécessaire, commencez la lecture.
1. Si une authentification est nécessaire, effectuez l’authentification en acquérant la licence.

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

   Cet exemple, pour simplifier, code explicitement le nom et le mot de passe de l’utilisateur.

   ```java
   DRMHelper.performDrmAuthentication(drmManager, drmMetadata, DRM_USERNAME, DRM_PASSWORD,  
     new DRMAuthenticationListener() { 
       @Override 
       public void onAuthenticationStart() { 
           Log.i(LOG_TAG + "#onAuthenticationStart", "DRM authentication started."); 
           // Spinner is already showing. 
       } 
       @Override 
       public void onAuthenticationError(int major, int minor, String errorString, String serverErrorURL) {  
           Log.e(LOG_TAG + "#onAuthenticationError", "DRM authentication failed. " +  
             major + " 0x" + Long.toHexString(minor)); 
           showToast(getString(R.string.drmAuthenticationError));   
           showLoadingSpinner(false); 
       } 
       @Override 
       public void onAuthenticationComplete(byte[] authenticationToken) { 
           Log.i(LOG_TAG + "#onAuthenticationComplete", "Auth successful. Launching content."); 
           showLoadingSpinner(false); 
           startPlayerActivity(ASSET_URL); 
       } 
   }); 
   ```

1. Cela implique également la communication réseau, d’où l’existence d’une opération asynchrone. Utilisez un écouteur de événement pour vérifier l’état de l’authentification.

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
       public void onAuthenticationError(int major, int minor,  
         String errorString, String serverErrorURL); 
   } 
   ```

1. Si l’authentification est réussie, lecture du début.
1. Si l’authentification échoue, avertissez l’utilisateur et ne début pas la lecture.

Votre application doit gérer toutes les erreurs d’authentification. Echec de l’authentification avant la lecture place TVSDK dans un état d’erreur. En d’autres termes, il change son état en ERROR, une erreur est générée contenant le code d’erreur de la bibliothèque DRM et la lecture s’arrête. Votre application doit résoudre le problème, réinitialiser le lecteur et recharger la ressource.

