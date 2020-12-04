---
seo-title: Délai d’expiration pour les jetons d’authentification
title: Délai d’expiration pour les jetons d’authentification
uuid: 41b0fbf5-a567-4118-bec1-c05e6e0b6d1f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# Délai d’expiration pour les jetons d’authentification{#timeout-for-authentication-tokens}

Tous les jetons d’authentification générés par le SDK d’accès à l’Adobe ont un délai d’expiration pour protéger la sécurité de l’application. L’expiration du jeton d’authentification est spécifiée, utilisez le SDK d’accès à l’Adobe lors du traitement d’une demande d’authentification. Une fois l’expiration passée, le jeton d’authentification n’est plus valide et l’utilisateur doit se réauthentifier auprès du serveur de licences.

Pour en savoir plus sur les demandes d&#39;authentification, voir AuthenticationHandler dans le *Adobe Access API Reference*.
