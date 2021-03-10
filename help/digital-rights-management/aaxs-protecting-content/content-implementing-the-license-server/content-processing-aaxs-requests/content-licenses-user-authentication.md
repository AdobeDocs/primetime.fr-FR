---
title: Authentification des utilisateurs
description: Authentification des utilisateurs
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Authentification de l&#39;utilisateur{#user-authentication}

Une demande d&#39;accès à un Adobe peut contenir un jeton d&#39;authentification.

Si l&#39;authentification par nom d&#39;utilisateur/mot de passe a été utilisée, la requête peut contenir un `AuthenticationToken` généré par le `AuthenticationHandler`. Pour accéder au jeton et le vérifier, utilisez `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d’utilisateur/mot de passe sur le client, utilisez l’ActionScript `DRMManager.authenticate()` ou l’API iOS.

Si le client et le serveur utilisent un mécanisme d’authentification personnalisé, le client obtient un jeton d’authentification par le biais d’un autre canal et définit le jeton d’authentification personnalisé à l’aide de l’API `DRMManager.setAuthenticationToken` ActionScript 3.0. Utilisez `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur est chargée de déterminer si le jeton d’authentification personnalisé est valide.
