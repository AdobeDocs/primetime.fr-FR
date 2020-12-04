---
description: L’élément clé côté client de la solution DRM Primetime est le Gestionnaire de DRM. L’exemple d’application inclus dans le SDK Android comprend également une classe DRMHelper qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.
seo-description: L’élément clé côté client de la solution DRM Primetime est le Gestionnaire de DRM. L’exemple d’application inclus dans le SDK Android comprend également une classe DRMHelper qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.
seo-title: Présentation de l’interface DRM de Primetime
title: Présentation de l’interface DRM de Primetime
uuid: d77a98c8-c1f5-4fe3-8d0b-3d21e288f228
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# Présentation de l&#39;interface DRM de Primetime {#primetime-drm-interface-overview}

L’élément clé côté client de la solution DRM Primetime est le Gestionnaire de DRM. L’exemple d’application inclus dans le SDK Android comprend également une classe DRMHelper qui peut être utilisée pour faciliter la mise en oeuvre de certaines opérations DRM.

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
   >Cette API retournera un objet `DRMManager` valide uniquement après le déclenchement de `MediaPlayerEvent.DRM_METADATA`. Si vous appelez `getDRMManager()` avant que ce événement ne se déclenche, il peut renvoyer la valeur NULL.

* La classe d&#39;assistance `DRMHelper`, utile lors de l&#39;implémentation de workflows DRM.
* Méthode de chargeur de métadonnées `DRMHelper`, qui charge les métadonnées DRM lorsqu’elles sont situées dans une URL distincte du média.

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

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Pour plus d&#39;informations sur la gestion des droits numériques, consultez la [documentation relative à la gestion des droits numériques](https://helpx.adobe.com/primetime/user-guide.html).
