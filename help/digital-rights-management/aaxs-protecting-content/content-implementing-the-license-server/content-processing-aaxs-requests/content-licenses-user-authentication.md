---
seo-title: Authentification des utilisateurs
title: Authentification des utilisateurs
uuid: 191964eb-cd68-47a6-8214-aec01f993df4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Authentification des utilisateurs{#user-authentication}

Une requête Adobe Access peut contenir un jeton d’authentification.

Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la requête peut contenir une `AuthenticationToken` génération par le `AuthenticationHandler`. Pour accéder au jeton et le vérifier, utilisez `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d’utilisateur/mot de passe sur le client, utilisez l’API `DRMManager.authenticate()` ActionScript ou iOS.

Si le client et le serveur utilisent un mécanisme d&#39;authentification personnalisé, le client obtient un jeton d&#39;authentification par l&#39;intermédiaire d&#39;un autre et définit le jeton d&#39;authentification personnalisé à l&#39;aide de l&#39;API `DRMManager.setAuthenticationToken` ActionScript 3.0. Utilisez `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur est chargée de déterminer si le jeton d’authentification personnalisé est valide.
