---
description: Pour utiliser des listes de révocation des certificats générées localement et des listes de mise à jour de stratégie, utilisez les API DRM d’Adobe Primetime pour vérifier la signature.
seo-description: Pour utiliser des listes de révocation des certificats générées localement et des listes de mise à jour de stratégie, utilisez les API DRM d’Adobe Primetime pour vérifier la signature.
seo-title: Consommation de listes CRL générées localement
title: Consommation de listes CRL générées localement
uuid: 2e20b8ca-8606-4c27-b585-2f020b93be32
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Consommation de listes CRL générées localement {#consuming-locally-generated-crls}

Pour utiliser des listes de révocation des certificats générées localement et des listes de mise à jour de stratégie, utilisez les API DRM d’Adobe Primetime pour vérifier la signature.

Les API suivantes vérifient que les listes n’ont pas été modifiées et que les listes ont été signées par le serveur de licences approprié :

* Appelez [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir la [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) à toute API.

   Pour plus d&#39;informations, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Appelez [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir la `PolicyUpdateList` à toute API.

   Pour plus d&#39;informations, voir [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

