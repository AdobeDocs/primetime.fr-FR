---
description: L’élément clé côté client de la solution DRM Primetime est le Gestionnaire de DRM. L’exemple d’application inclus dans le SDK Android comprend également une classe DRMHelper qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.
seo-description: L’élément clé côté client de la solution DRM Primetime est le Gestionnaire de DRM. L’exemple d’application inclus dans le SDK Android comprend également une classe DRMHelper qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.
seo-title: Présentation de l’interface DRM de Primetime
title: Présentation de l’interface DRM de Primetime
uuid: 9e6f6ae6-7193-40fe-bc9d-d8de33705f5d
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Présentation de l’interface DRM de Primetime {#primetime-drm-interface-overview}

L’élément clé côté client de la solution DRM Primetime est le Gestionnaire de DRM. L’exemple d’application inclus dans le SDK Android comprend également une `DRMHelper` classe qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.

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
   >Cette API retournera un `DRMManager` objet valide uniquement après le `MediaPlayerEvent.DRM_METADATA` déclenchement. Si vous appelez `getDRMManager()` avant le déclenchement de ce événement, il peut renvoyer la valeur NULL.

* Classe `DRMHelper` d’assistance, utile lors de l’implémentation de workflows DRM.
* Méthode de chargement `DRMHelper` des métadonnées, qui charge les métadonnées DRM lorsqu’elles sont situées dans une URL distincte du média.

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* Méthode `DRMHelper` permettant de vérifier les métadonnées DRM et de déterminer si une authentification est requise.

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

* Événements qui informent votre application de diverses activités et de l’état de DRM.

Pour plus d’informations sur DRM, consultez la documentation [](https://helpx.adobe.com/primetime/user-guide.html)DRM.
