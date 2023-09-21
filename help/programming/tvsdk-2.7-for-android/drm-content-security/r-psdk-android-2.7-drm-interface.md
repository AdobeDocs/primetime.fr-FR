---
description: L’élément clé côté client de la solution DRM Primetime est DRM Manager. L’exemple d’application inclus avec le SDK Android comprend également une classe DRMHelper qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.
title: Présentation de l’interface DRM Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Présentation de l’interface DRM Primetime {#primetime-drm-interface-overview}

L’élément clé côté client de la solution DRM Primetime est DRM Manager. L’exemple d’application inclus avec le SDK Android comprend également une classe DRMHelper qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM fournit un workflow évolutif et efficace pour mettre en oeuvre la protection du contenu dans les applications TVSDK. Vous protégez et gérez les droits sur votre contenu vidéo en créant une licence pour chaque fichier multimédia numérique.

Pour plus d’informations, voir l’exemple de code du lecteur DRM inclus dans le package TVSDK.

Voici les éléments d’API les plus importants pour travailler avec DRM :

* Référence dans le lecteur multimédia à l’objet du gestionnaire DRM qui implémente le sous-système DRM :

  ```java
  MediaPlayer.getDRMManager();
  ```

  >[!TIP]
  >
  >Cette API renverra un `DRMManager` uniquement après l’objet `MediaPlayerEvent.DRM_METADATA` est déclenché. Si vous appelez `getDRMManager()` avant que cet événement ne se déclenche, il peut renvoyer la valeur NULL.

* La variable `DRMHelper` classe d’assistance, utile lors de la mise en oeuvre des processus DRM.
* A `DRMHelper` méthode de chargeur de métadonnées qui charge les métadonnées DRM lorsqu’elles se trouvent dans une URL distincte du média.

  ```java
  public static void loadDRMMetadata(final DRMManager drmManager,  
     final String drmMetadataUrl,  
     final DRMLoadMetadataListener loadMetadataListener);
  ```

* A `DRMHelper` pour vérifier les métadonnées DRM et déterminer si une authentification est requise.

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

* Événements qui informent votre application de divers statuts et activités DRM.

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Pour plus d’informations sur DRM, voir [Documentation DRM](https://helpx.adobe.com/primetime/user-guide.html).
