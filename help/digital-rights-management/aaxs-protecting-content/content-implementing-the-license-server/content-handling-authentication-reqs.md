---
seo-title: Gestion des demandes d’authentification
title: Gestion des demandes d’authentification
uuid: 036582d4-611c-4772-b247-81a3144fd5d6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---


# Gestion des demandes d’authentification{#handling-authentication-requests}

La classe `AuthenticationHandler` est utilisée pour traiter les demandes d&#39;authentification. Il est utilisé uniquement pour l’authentification par nom d’utilisateur/mot de passe.

Lors de la génération du jeton d’authentification, la date d’expiration du jeton doit être spécifiée. Les propriétés personnalisées peuvent également être incluses dans le jeton. Si elles sont définies, ces propriétés seront visibles pour le serveur lorsque le jeton d’authentification est envoyé dans les demandes suivantes. Voir [Gestion des demandes de licence](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-handling-license-reqs.md) pour plus d’informations sur la gestion des jetons d’authentification personnalisés.

Le gestionnaire lit une demande d&#39;authentification et analyse le message de la demande lorsque `parseRequest()` est appelé. L&#39;implémentation du serveur examine les informations d&#39;identification de l&#39;utilisateur dans la requête et, si les informations d&#39;identification sont valides, génère un objet `AuthenticationToken` en appelant `getRequest().generateAuthToken()`. Si `AuthenticationRequestMessage.generateAuthToken()` n&#39;est pas appelé avant `close()`, un code d&#39;erreur d&#39;authentification est envoyé.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de demande est &quot;URL du serveur de licence dans les métadonnées : + &quot;/flashaccess/authn/v4&quot;. Si le protocole version 3 est le maximum pris en charge par le client ou le serveur, les clients Adobe Access envoient des demandes d&#39;authentification à &quot;License Server URL in metadata&quot; + &quot;/flashaccess/authn/v3&quot;. Sinon, les demandes d’authentification sont envoyées à &quot;l’URL du serveur de licences dans les métadonnées&quot; + &quot;/flashaccess/authn/v1&quot;

