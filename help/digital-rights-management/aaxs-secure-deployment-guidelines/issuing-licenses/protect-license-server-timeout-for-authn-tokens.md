---
title: Délai d’expiration pour les jetons d’authentification
description: Délai d’expiration pour les jetons d’authentification
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# Délai d’expiration pour les jetons d’authentification{#timeout-for-authentication-tokens}

Tous les jetons d’authentification générés par le SDK d’accès à l’Adobe ont un délai d’expiration pour protéger la sécurité de l’application. L’expiration du jeton d’authentification est spécifiée, utilisez le SDK d’accès à l’Adobe lors du traitement d’une demande d’authentification. Une fois l’expiration passée, le jeton d’authentification n’est plus valide et l’utilisateur doit se réauthentifier auprès du serveur de licences.

Pour en savoir plus sur les demandes d&#39;authentification, voir AuthenticationHandler dans le *Adobe Access API Reference*.
