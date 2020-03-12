---
seo-title: ' de licence'
title: ' de licence'
uuid: 61ff171f-b977-40ef-8e8d-2900316fa89a
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


#  de licence {#license-preview}

Si vous vous demandez si un périphérique peut consommer et appliquer intégralement une licence DRM Primetime, vous pouvez utiliser la fonction  de licence. Une licence  correspond entièrement à toutes les contraintes et restrictions définies dans la licence finale, mais ne contient pas la clé de chiffrement de contenu (CEK) nécessaire pour déchiffrer le contenu protégé. Cette fonctionnalité est utile pour déterminer si le client peut effectivement consommer la licence avant que le serveur de distribution de contenu ne décide de fournir une licence particulière au client. Par exemple, un client souhaite regarder le contenu HD, mais le distributeur de contenu souhaite s’assurer que le périphérique peut détecter et utiliser le HDCP. Dans ce cas, le client peut appeler `DRMManager.loadPreviewVoucher()`. Si une licence `DRMStatusEvent` est reçue, au lieu d’une `DRMErrorEvent`, il est confirmé que le client peut appliquer intégralement les restrictions de la protection d’Output dans la licence et que le serveur de distribution de contenu peut librement fournir ce type de licence au client.

[iOS acquisitionPreviewLicense :](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a3baac603bdd8826624dbe97f9faaba10)

[Android acquisitionPreviewLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquirePreviewLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))
