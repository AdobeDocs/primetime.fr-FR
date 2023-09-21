---
description: Pour utiliser des listes de révocation des certificats (CRL) générées localement et des listes de mise à jour de stratégie, utilisez les API DRM Adobe Primetime pour vérifier la signature.
title: Consommation de listes CRL générées localement
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Consommation de listes CRL générées localement {#consuming-locally-generated-crls}

Pour utiliser des listes de révocation des certificats (CRL) générées localement et des listes de mise à jour de stratégie, utilisez les API DRM Adobe Primetime pour vérifier la signature.

Les API suivantes vérifient que les listes n’ont pas été modifiées et que les listes ont été signées par le bon serveur de licences :

* Appeler [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir l’événement [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) à toute API.

  Pour plus d’informations, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Appeler [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) pour vérifier la signature avant de fournir l’événement `PolicyUpdateList` à toute API.

  Pour plus d’informations, voir [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

