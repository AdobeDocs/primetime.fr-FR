---
seo-title: Authentification des utilisateurs
title: Authentification des utilisateurs
uuid: 191964eb-cd68-47a6-8214-aec01f993df4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Authentification de l&#39;utilisateur{#user-authentication}

Une demande d&#39;accès à un Adobe peut contenir un jeton d&#39;authentification.

Si l&#39;authentification par nom d&#39;utilisateur/mot de passe a été utilisée, la requête peut contenir un `AuthenticationToken` généré par le `AuthenticationHandler`. Pour accéder au jeton et le vérifier, utilisez `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d’utilisateur/mot de passe sur le client, utilisez l’ActionScript `DRMManager.authenticate()` ou l’API iOS.

Si le client et le serveur utilisent un mécanisme d’authentification personnalisé, le client obtient un jeton d’authentification par le biais d’un autre canal et définit le jeton d’authentification personnalisé à l’aide de l’API `DRMManager.setAuthenticationToken` ActionScript 3.0. Utilisez `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur est chargée de déterminer si le jeton d’authentification personnalisé est valide.
