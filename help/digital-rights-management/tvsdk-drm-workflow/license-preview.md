---
title: Aperçu de la licence
description: Aperçu de la licence
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Aperçu de la licence {#license-preview}

Si une question se pose concernant la possibilité pour un appareil d’utiliser et d’appliquer pleinement une licence Primetime DRM, vous pouvez utiliser la fonction Aperçu de la licence . Une licence d’aperçu correspond entièrement à toutes les contraintes et restrictions définies dans la licence finale, mais ne contient pas la clé de chiffrement de contenu (CEK) nécessaire pour déchiffrer le contenu protégé. Cette fonctionnalité est utile pour déterminer si le client peut effectivement utiliser la licence avant que le Distributeur de contenu ne décide de fournir une licence spécifique au client. Par exemple, un client souhaite regarder le contenu HD, mais le fournisseur de contenu souhaite s’assurer que l’appareil peut détecter et interagir pleinement avec HDCP. Dans ce cas, le client peut appeler `DRMManager.loadPreviewVoucher()`. Si une `DRMStatusEvent` est reçu, au lieu d’un `DRMErrorEvent`, il est ensuite confirmé que le client peut pleinement appliquer les restrictions de protection de sortie dans la licence, et que le Distributeur de contenu peut fournir librement ce type de licence au client.

[iOS acquirePreviewLicense :](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a3baac603bdd8826624dbe97f9faaba10)

[Android acquirePreviewLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquirePreviewLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))
