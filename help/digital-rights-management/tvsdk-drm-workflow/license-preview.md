---
seo-title: Prévisualisation de licence
title: Prévisualisation de licence
uuid: 61ff171f-b977-40ef-8e8d-2900316fa89a
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Prévisualisation de licence {#license-preview}

Si une question se pose quant à savoir si un périphérique peut consommer et appliquer une licence DRM Primetime, vous pouvez utiliser la fonction Prévisualisation de licence. Une licence de Prévisualisation correspond entièrement à toutes les contraintes et restrictions définies dans la licence finale, mais ne contient pas la clé de chiffrement de contenu (CEK) nécessaire pour déchiffrer le contenu protégé. Cette fonctionnalité est utile pour déterminer si le client peut effectivement consommer la licence avant que le distributeur de contenu ne décide de fournir une licence particulière au client. Par exemple, un client souhaite regarder le contenu HD, mais le distributeur de contenu souhaite s’assurer que l’appareil peut détecter et utiliser pleinement HDCP. Dans ce cas, le client peut appeler `DRMManager.loadPreviewVoucher()`. Si un `DRMStatusEvent` est reçu, au lieu d&#39;un `DRMErrorEvent`, il est confirmé que le client peut appliquer pleinement les restrictions de protection d&#39;Output dans la licence et que le distributeur de contenu peut fournir librement ce type de licence au client.

[iOS acquisitionPreviewLicense :](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a3baac603bdd8826624dbe97f9faaba10)

[Android acquisitionPreviewLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquirePreviewLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))
