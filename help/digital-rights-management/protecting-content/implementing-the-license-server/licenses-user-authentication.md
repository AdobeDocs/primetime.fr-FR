---
title: Authentification de l’utilisateur
description: Authentification de l’utilisateur
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Authentification de l’utilisateur {#user-authentication}

Une requête DRM Adobe Primetime peut contenir un jeton d’authentification.

Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la demande peut inclure une `AuthenticationToken` généré par la variable `AuthenticationHandler`. Si vous souhaitez accéder au jeton et le vérifier, vous devez utiliser `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d’utilisateur/mot de passe sur le client, utilisez la variable `DRMManager.authenticate()` API ActionScript ou iOS.

Si le client et le serveur utilisent un mécanisme d’authentification personnalisé, le client obtient un jeton d’authentification par le biais d’un autre canal et définit le jeton d’authentification personnalisé à l’aide de la variable `DRMManager.setAuthenticationToken` API ActionScript 3.0. Utilisation `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur détermine si le jeton d’authentification personnalisé est valide.
