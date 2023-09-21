---
title: Gestion des demandes d’authentification
description: Gestion des demandes d’authentification
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Gestion des demandes d’authentification{#handling-authentication-requests}

La variable `AuthenticationHandler` est utilisée pour traiter les demandes d’authentification. Il est utilisé uniquement pour l’authentification par nom d’utilisateur/mot de passe.

Lors de la génération du jeton d’authentification, la date d’expiration du jeton doit être spécifiée. Les propriétés personnalisées peuvent également être incluses dans le jeton. Si elles sont définies, ces propriétés seront visibles par le serveur lorsque le jeton d’authentification est envoyé dans les demandes suivantes. Voir [Gestion des demandes de licence](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-handling-license-reqs.md) pour plus d’informations sur la gestion des jetons d’authentification personnalisés.

Le gestionnaire lit une demande d’authentification et analyse le message de demande lors de la `parseRequest()` est appelée. L’implémentation du serveur examine les informations d’identification de l’utilisateur dans la requête. Si les informations d’identification sont valides, génère une `AuthenticationToken` en appelant `getRequest().generateAuthToken()`. If `AuthenticationRequestMessage.generateAuthToken()` n’est pas appelé avant `close()`, un code d’erreur d’échec d’authentification est envoyé.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* La classe de message de requête est `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de demande est &quot;URL du serveur de licences dans les métadonnées : + &quot;/flashaccess/authn/v4&quot;. Si le protocole version 3 est le maximum pris en charge par le client ou le serveur, les clients Adobe Access envoient des demandes d’authentification à &quot;URL du serveur de licences dans les métadonnées&quot; + &quot;/flashaccess/authn/v3&quot;. Sinon, les demandes d’authentification sont envoyées à &quot;URL du serveur de licences dans les métadonnées&quot; + &quot;/flashaccess/authn/v1&quot;
