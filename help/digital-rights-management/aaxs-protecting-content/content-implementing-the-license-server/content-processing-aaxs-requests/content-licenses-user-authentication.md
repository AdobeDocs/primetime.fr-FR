---
title: Authentification de l’utilisateur
description: Authentification de l’utilisateur
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Authentification de l’utilisateur{#user-authentication}

Une demande d’accès à un Adobe peut contenir un jeton d’authentification.

Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la requête peut contenir une `AuthenticationToken` généré par la variable `AuthenticationHandler`. Pour accéder au jeton et le vérifier, utilisez `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d’utilisateur/mot de passe sur le client, utilisez la variable `DRMManager.authenticate()` API ActionScript ou iOS.

Si le client et le serveur utilisent un mécanisme d’authentification personnalisé, le client obtient un jeton d’authentification par le biais d’un autre canal et définit le jeton d’authentification personnalisé à l’aide de la variable `DRMManager.setAuthenticationToken` API ActionScript 3.0. Utilisation `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur est chargée de déterminer si le jeton d’authentification personnalisé est valide.
