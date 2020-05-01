---
seo-title: Authentification des utilisateurs
title: Authentification des utilisateurs
uuid: 5cbd76b9-ff64-4a4b-8cfd-54f05c04eaa3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Authentification des utilisateurs {#user-authentication}

Une demande DRM Adobe Primetime peut contenir un jeton d’authentification.

Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la requête peut inclure une requête `AuthenticationToken` générée par le `AuthenticationHandler`. Si vous souhaitez accéder au jeton et le vérifier, vous devez l’utiliser `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d&#39;utilisateur/mot de passe sur le client, utilisez l&#39;API `DRMManager.authenticate()` ActionScript ou iOS.

Si le client et le serveur utilisent un mécanisme d&#39;authentification personnalisé, le client obtient un jeton d&#39;authentification par le biais d&#39;un autre canal et définit le jeton d&#39;authentification personnalisé à l&#39;aide de l&#39;API `DRMManager.setAuthenticationToken` ActionScript 3.0. Utilisez `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur détermine si le jeton d’authentification personnalisé est valide.
