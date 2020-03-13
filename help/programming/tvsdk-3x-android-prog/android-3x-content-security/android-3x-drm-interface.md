---
description: L’élément clé côté client de la solution DRM Primetime est DRM Manager. L’exemple d’application inclus dans le SDK Android inclut également une classe DRMHelper qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.
seo-description: L’élément clé côté client de la solution DRM Primetime est DRM Manager. L’exemple d’application inclus dans le SDK Android inclut également une classe DRMHelper qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.
seo-title: Présentation de l’interface DRM Primetime
title: Présentation de l’interface DRM Primetime
uuid: 9e6f6ae6-7193-40fe-bc9d-d8de33705f5d
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Présentation de l’interface DRM Primetime {#primetime-drm-interface-overview}

L’élément clé côté client de la solution DRM Primetime est DRM Manager. L’exemple d’application inclus dans le SDK Android comprend également une `DRMHelper` classe qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM offre un flux de travail évolutif et efficace pour mettre en oeuvre la protection du contenu dans les applications TVSDK. Vous protégez et gérez les droits sur votre contenu vidéo en créant une licence pour chaque fichier multimédia numérique.

Pour plus d’informations, voir l’exemple de code du lecteur DRM inclus dans le package TVSDK.

Voici les principaux éléments d’API pour travailler avec DRM :

* Référence dans le lecteur multimédia à l’objet du gestionnaire DRM qui implémente le sous-système DRM :

   ```java
   MediaPlayer.getDRMManager();
   ```

   >[!TIP]
   >
   >Cette API ne renvoie un `DRMManager` objet valide qu’après le `MediaPlayerEvent.DRM_METADATA` déclenchement. Si vous appelez `getDRMManager()` avant que ce ne se déclenche, il peut renvoyer la valeur NULL.

* Classe `DRMHelper` d’assistance, utile lors de l’implémentation des  DRM.
* Méthode `DRMHelper` de chargeur de métadonnées, qui charge les métadonnées DRM lorsqu’elles se trouvent dans une URL distincte du média.

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* Méthode `DRMHelper` permettant de vérifier les métadonnées DRM et de déterminer si l’authentification est requise.

   ```java
   /** 
   * Return whether authentication is needed for the provided 
   * DRMMetadata. 
   * 
   * @param drmMetadata 
   * The desired DRMMetadata on which to check whether auth is needed. 
   * @return whether authentication is required for the provided metadata 
   */ 
   public static boolean isAuthNeeded(DRMMetadata drmMetadata);
   ```

* `DRMHelper` pour effectuer l’authentification.

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
   * @param authUser 
   * the DRM username provider by the user. 
   * @param authPass 
   * the DRM password provided by the user. 
   */ 
   public static void performDrmAuthentication(final DRMManager drmManager,  
   final DRMMetadata drmMetadata,  
   final String authUser,  
   final String authPass,  
   final DRMAuthenticationListener authenticationListener);
   ```

* qui avise votre application de divers et de l’état et de l’ de DRM.

Pour plus d’informations sur DRM, voir la documentation [](https://helpx.adobe.com/primetime/user-guide.html)DRM.
