---
description: Tous les jetons d’authentification générés par le SDK DRM d’Adobe Primetime ont un délai d’expiration pour protéger la sécurité de l’application.
seo-description: Tous les jetons d’authentification générés par le SDK DRM d’Adobe Primetime ont un délai d’expiration pour protéger la sécurité de l’application.
seo-title: Délai d’expiration pour les jetons d’authentification
title: Délai d’expiration pour les jetons d’authentification
uuid: 2c2b0dad-0979-4d49-b109-2700ceb4d722
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# Délai d’expiration pour les jetons d’authentification{#timeout-for-authentication-tokens}

Tous les jetons d’authentification générés par le SDK DRM d’Adobe Primetime ont un délai d’expiration pour protéger la sécurité de l’application.

L’expiration du jeton d’authentification est spécifiée à l’aide du SDK DRM Primetime lors du traitement d’une demande d’authentification. Une fois arrivé à expiration, le jeton n’est plus valide et l’utilisateur doit s’authentifier à nouveau auprès du serveur de licences.

Pour en savoir plus sur les demandes d’authentification, voir [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).
