---
description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour assurer un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution DRM intégrée d’Adobe Primetime.
seo-description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour assurer un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution DRM intégrée d’Adobe Primetime.
seo-title: Présentation de l’interface DRM Primetime
title: Présentation de l’interface DRM Primetime
uuid: 71479464-8356-4732-9774-da9f6084e6ad
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Présentation {#primetime-drm-interface-overview}

Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour assurer un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution DRM intégrée d’Adobe Primetime.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Consultez votre représentant Adobe pour obtenir les informations les plus récentes sur la disponibilité des solutions DRM tierces.

L’élément clé côté client du système de gestion des droits numériques (DRM) de Primetime est le gestionnaire de gestion des droits numériques (DRM). L’exemple d’application fourni avec le SDK Android comprend une `DRMHelper` classe qui montre comment faciliter la mise en oeuvre de certaines opérations DRM.

Primetime DRM offre un flux de travail évolutif et efficace pour mettre en oeuvre la protection du contenu dans les applications TVSDK. Vous protégez et gérez les droits sur votre contenu vidéo en créant une licence pour chaque fichier multimédia numérique.

Reportez-vous à l’exemple de code du lecteur DRM inclus dans le package TVSDK.

Voici les principaux éléments d’API pour travailler avec DRM :

* Référence dans le lecteur multimédia à l’objet du gestionnaire DRM qui implémente le sous-système DRM :

   ```java
   MediaPlayer.getDRMManager();
   ```

   >[!TIP]
   >
   >Cette API ne renvoie un `DRMManager` objet valide qu’après le `MediaPlayerEvent.DRM_METADATA` déclenchement. Si vous appelez `getDRMManager()` avant que ce ne se déclenche, il peut renvoyer la valeur NULL.

* Classe `DRMHelper` d’assistance, utile lors de l’implémentation des  DRM.

   Vous pouvez voir `DRMHelper` à `ReferencePlayer`.

* Méthode `DRMHelper` de chargeur de métadonnées, qui charge les métadonnées DRM lorsqu’elles se trouvent dans une URL distincte du média.

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* Méthode `DRMHelper` permettant de vérifier les métadonnées DRM afin de déterminer si l’authentification est nécessaire.

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

Pour plus d’informations sur DRM, consultez la documentation [d’](https://helpx.adobe.com/primetime/user-guide.html)Adobe Primetime DRM.
