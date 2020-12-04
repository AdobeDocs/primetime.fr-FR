---
seo-title: Gestion des erreurs de demande de licence
title: Gestion des erreurs de demande de licence
uuid: 4563f546-77fe-4fb9-9ad8-a0689fe6fb4d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Gestion des erreurs de demande de licence {#license-request-error-handling}

Si une erreur se produit lors de l&#39;analyse de la requête, un `HandlerParsingException` se produit. Cette exception comprend les informations d’erreur renvoyées au client. Si vous devez récupérer les informations d&#39;erreur, vous devez appeler `HandlerParsingException.getErrorData()`. Si une erreur se produit lors de la génération d&#39;une licence en raison des exigences de la stratégie DRM qui n&#39;ont pas été satisfaites, un `PolicyEvaluationException` se produit. Cette exception inclut également `ErrorData` à renvoyer au client.

Consultez la documentation de l&#39;API pour `LicenseRequestMessage.generateLicense()` pour plus d&#39;informations sur la manière dont les stratégies DRM sont évaluées lors de la génération de la licence.
