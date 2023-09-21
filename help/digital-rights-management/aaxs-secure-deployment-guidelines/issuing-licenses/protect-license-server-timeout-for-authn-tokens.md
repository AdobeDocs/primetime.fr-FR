---
title: Timeout des jetons d’authentification
description: Timeout des jetons d’authentification
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Timeout des jetons d’authentification{#timeout-for-authentication-tokens}

Tous les jetons d’authentification générés par le SDK Adobe Access ont un délai d’expiration pour protéger la sécurité de l’application. L’expiration du jeton d’authentification est spécifiée à l’aide du SDK Adobe Access lors du traitement d’une demande d’authentification. Une fois l’expiration passée, le jeton d’authentification n’est plus valide et l’utilisateur doit se réauthentifier auprès du serveur de licences.

Pour en savoir plus sur les demandes d’authentification, voir AuthenticationHandler dans la section *Référence de l’API Adobe Access*.
