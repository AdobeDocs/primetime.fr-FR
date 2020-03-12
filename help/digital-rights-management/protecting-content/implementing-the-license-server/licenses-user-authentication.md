---
seo-title: Authentification des utilisateurs
title: Authentification des utilisateurs
uuid: 5cbd76b9-ff64-4a4b-8cfd-54f05c04eaa3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Authentification des utilisateurs {#user-authentication}

Une requête DRM Adobe Primetime peut contenir un jeton d’authentification.

Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la requête peut inclure une `AuthenticationToken` générée par le `AuthenticationHandler`. Si vous souhaitez accéder au jeton et le vérifier, vous devez l’utiliser `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d’utilisateur/mot de passe sur le client, utilisez l’API `DRMManager.authenticate()` ActionScript ou iOS.

Si le client et le serveur utilisent un mécanisme d’authentification personnalisé, le client obtient un jeton d’authentification par l’intermédiaire d’un autre et définit le jeton d’authentification personnalisé à l’aide de l’API `DRMManager.setAuthenticationToken` ActionScript 3.0. Utilisez `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur détermine si le jeton d’authentification personnalisé est valide.
