---
description: Tous les jetons d’authentification générés par le SDK DRM Adobe Primetime ont un délai d’expiration pour protéger la sécurité de l’application.
title: Délai d’expiration pour les jetons d’authentification
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# Délai d’expiration pour les jetons d’authentification{#timeout-for-authentication-tokens}

Tous les jetons d’authentification générés par le SDK DRM Adobe Primetime ont un délai d’expiration pour protéger la sécurité de l’application.

L’expiration du jeton d’authentification est spécifiée, utilisez le SDK DRM Primetime lors du traitement d’une demande d’authentification. Une fois arrivé à expiration, le jeton n’est plus valide et l’utilisateur doit s’authentifier de nouveau auprès du serveur de licences.

Pour en savoir plus sur les demandes d’authentification, voir [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).
