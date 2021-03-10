---
title: Gestion des erreurs de demande de licence
description: Gestion des erreurs de demande de licence
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Gestion des erreurs de demande de licence {#license-request-error-handling}

Si une erreur se produit lors de l&#39;analyse de la requête, un `HandlerParsingException` se produit. Cette exception comprend les informations d’erreur renvoyées au client. Si vous devez récupérer les informations d&#39;erreur, vous devez appeler `HandlerParsingException.getErrorData()`. Si une erreur se produit lors de la génération d&#39;une licence en raison des exigences de la stratégie DRM qui n&#39;ont pas été satisfaites, un `PolicyEvaluationException` se produit. Cette exception inclut également `ErrorData` à renvoyer au client.

Consultez la documentation de l&#39;API pour `LicenseRequestMessage.generateLicense()` pour plus d&#39;informations sur la manière dont les stratégies DRM sont évaluées lors de la génération de la licence.
