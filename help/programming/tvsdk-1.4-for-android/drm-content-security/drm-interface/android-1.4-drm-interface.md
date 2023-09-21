---
description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour fournir un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces comme alternative à la solution DRM intégrée de Primetime d’Adobe.
title: Présentation de l’interface DRM Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Présentation {#primetime-drm-interface-overview}

Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour fournir un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces comme alternative à la solution DRM intégrée de Primetime d’Adobe.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Consultez le représentant de votre Adobe pour obtenir les informations les plus récentes sur la disponibilité de solutions DRM tierces.

Le DRM est l’élément clé du système de gestion des droits numériques (DRM) de Primetime côté client. L’exemple d’application fourni avec le SDK Android comprend une `DRMHelper` qui montre comment faciliter la mise en oeuvre de certaines opérations DRM.

Primetime DRM fournit un workflow évolutif et efficace pour mettre en oeuvre la protection du contenu dans les applications TVSDK. Vous protégez et gérez les droits sur votre contenu vidéo en créant une licence pour chaque fichier multimédia numérique.

Reportez-vous à l’exemple de code du lecteur DRM inclus dans le package TVSDK.

Voici les éléments d’API les plus importants pour travailler avec DRM :

* Référence dans le lecteur multimédia à l’objet du gestionnaire DRM qui implémente le sous-système DRM :

  ```java
  MediaPlayer.getDRMManager();
  ```

  >[!TIP]
  >
  >Cette API renverra un `DRMManager` uniquement après l’objet `MediaPlayerEvent.DRM_METADATA` est déclenché. Si vous appelez `getDRMManager()` avant que cet événement ne se déclenche, il peut renvoyer la valeur NULL.

* La variable `DRMHelper` classe d’assistance, utile lors de la mise en oeuvre des processus DRM.

  Vous pouvez voir `DRMHelper` in `ReferencePlayer`.

* A `DRMHelper` méthode de chargeur de métadonnées qui charge les métadonnées DRM lorsqu’elles se trouvent dans une URL distincte du média.

  ```java
  public static void loadDRMMetadata(final DRMManager drmManager,  
     final String drmMetadataUrl,  
     final DRMLoadMetadataListener loadMetadataListener);
  ```

* A `DRMHelper` pour vérifier les métadonnées DRM afin de déterminer si une authentification est nécessaire.

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

<!--<a id="section_899BD9061D484E1BBA46E84617C36867"></a>-->

Autres éléments d’API pertinents :

* [com.adobe.ave.drm.DRMManager](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMManager.html)
* [com.adobe.ave.drm.DRMMetdata](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMMetadata.html)
* [com.adobe.ave.drm.DRMPolicy](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMPolicy.html)
* [com.adobe.ave.drm.DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMAuthenticationMethod.html)
* [com.adobe.ave.drm.DRMAuthenticationCompleteCallback](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMAuthenticationCompleteCallback.html)
* [com.adobe.ave.drm.DRMOperationErrorCallback](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMOperationErrorCallback.html)
* com.adobe.mediacore.drm.DRMAuthenticateListener

<!-- 
Comment Type: draft
(https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/drm/DRMAuthenticateListener.html)

-->
<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Pour plus d’informations sur DRM, voir [Documentation Adobe Primetime DRM](https://helpx.adobe.com/primetime/user-guide.html).
