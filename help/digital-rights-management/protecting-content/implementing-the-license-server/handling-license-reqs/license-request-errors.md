---
seo-title: Gestion des erreurs de demande de licence
title: Gestion des erreurs de demande de licence
uuid: 4563f546-77fe-4fb9-9ad8-a0689fe6fb4d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gestion des erreurs de demande de licence {#license-request-error-handling}

Si une erreur se produit lors de l’analyse de la requête, une erreur `HandlerParsingException` se produit. Cette exception inclut les informations d’erreur renvoyées au client. Si vous devez récupérer les informations d’erreur, vous devez appeler `HandlerParsingException.getErrorData()`. Si une erreur se produit lors de la génération d’une licence en raison des exigences de la stratégie DRM qui n’ont pas été satisfaites, une erreur `PolicyEvaluationException` se produit. Cette exception inclut également le renvoi `ErrorData` au client.

Consultez la documentation de l’API pour plus d’informations `LicenseRequestMessage.generateLicense()` sur la manière dont les stratégies DRM sont évaluées lors de la génération de la licence.
