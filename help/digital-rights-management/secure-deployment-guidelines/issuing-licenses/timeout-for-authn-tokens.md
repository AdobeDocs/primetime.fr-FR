---
description: Tous les jetons d’authentification générés par le SDK Adobe Primetime DRM ont un délai d’expiration pour protéger la sécurité de l’application.
title: Timeout des jetons d’authentification
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# Timeout des jetons d’authentification{#timeout-for-authentication-tokens}

Tous les jetons d’authentification générés par le SDK Adobe Primetime DRM ont un délai d’expiration pour protéger la sécurité de l’application.

L’expiration du jeton d’authentification est spécifiée à l’aide du SDK DRM Primetime lors de la gestion d’une demande d’authentification. Une fois expiré, le jeton n’est plus valide et l’utilisateur doit s’authentifier à nouveau auprès du serveur de licences.

Pour en savoir plus sur les demandes d’authentification, voir [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).
