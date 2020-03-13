---
description: Pour utiliser les  de révocation des certificats (CRL) générées localement et les de mise à jour des stratégies, utilisez les API DRM d’Adobe Primetime pour vérifier la signature.
seo-description: Pour utiliser les  de révocation des certificats (CRL) générées localement et les de mise à jour des stratégies, utilisez les API DRM d’Adobe Primetime pour vérifier la signature.
seo-title: Consommation de listes CRL générées localement
title: Consommation de listes CRL générées localement
uuid: 2e20b8ca-8606-4c27-b585-2f020b93be32
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Consommation de listes CRL générées localement {#consuming-locally-generated-crls}

Pour utiliser les  de révocation des certificats (CRL) générées localement et les de mise à jour des stratégies, utilisez les API DRM d’Adobe Primetime pour vérifier la signature.

Les API suivantes vérifient que le  du n’a pas été modifié et que le  a été signé par le serveur de licence approprié :

* Appelez [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir la [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) à toute API.

   Pour plus d’informations, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Appelez [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir le `PolicyUpdateList` à toute API.

   Pour plus d’informations, voir [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

