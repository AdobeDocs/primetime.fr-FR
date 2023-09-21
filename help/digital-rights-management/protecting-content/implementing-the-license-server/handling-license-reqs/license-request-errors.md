---
title: Gestion des erreurs de demande de licence
description: Gestion des erreurs de demande de licence
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Gestion des erreurs de demande de licence {#license-request-error-handling}

Si une erreur se produit lors de l’analyse de la requête, une `HandlerParsingException` survient. Cette exception inclut des informations d’erreur renvoyées au client. Si vous devez récupérer les informations d’erreur, vous devez appeler `HandlerParsingException.getErrorData()`. Si une erreur se produit lors de la génération d’une licence en raison des exigences de la stratégie DRM qui n’ont pas été satisfaites, une `PolicyEvaluationException` survient. Cette exception inclut également `ErrorData` à renvoyer au client.

Consultez la documentation de l’API pour `LicenseRequestMessage.generateLicense()` pour plus d’informations sur la manière dont les stratégies DRM sont évaluées lors de la génération de la licence.
