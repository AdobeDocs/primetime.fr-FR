---
seo-title: Gestion des demandes d’authentification
title: Gestion des demandes d’authentification
uuid: abcb9cf6-668e-405c-9659-9ed1bcc33024
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gestion des demandes d’authentification {#handle-authentication-requests}

La `AuthenticationHandler` classe est utilisée pour traiter les demandes d&#39;authentification. Il est utilisé uniquement pour l’authentification par nom d’utilisateur/mot de passe.

Lors de la génération du jeton d’authentification, la date d’expiration du jeton doit être spécifiée. Les propriétés personnalisées peuvent également être incluses dans le jeton. Si elles sont définies, ces propriétés seront visibles pour le serveur lorsque le jeton d’authentification est envoyé dans les demandes suivantes. Voir [Gestion des demandes](../../protecting-content/implementing-the-license-server/handling-license-reqs/license-handling-classes.md) de licence pour en savoir plus sur la gestion des jetons d’authentification personnalisés.

Le gestionnaire lit une demande d’authentification et analyse le message de la demande lors de l’ `parseRequest()` appel. L’implémentation du serveur examine les informations d’identification de l’utilisateur dans la requête et, si les informations d’identification sont valides, génère un `AuthenticationToken` objet en appelant `getRequest().generateAuthToken()`. Si `AuthenticationRequestMessage.generateAuthToken()` n’est pas appelé avant `close()`, un code d’erreur d’authentification est envoyé.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de demande est &quot;URL du serveur de licence dans les métadonnées : + &quot; [!DNL /flashaccess/authn/v4]&quot;. Si le protocole version 3 est le maximum pris en charge par le client ou le serveur, les clients DRM d’Adobe Primetime envoient alors les demandes d’authentification à &quot;License Server URL in metadata&quot; + &quot; [!DNL /flashaccess/authn/v3]&quot;. Sinon, les demandes d’authentification sont envoyées à &quot;l’URL du serveur de licences dans les métadonnées&quot; + &quot; [!DNL /flashaccess/authn/v1]&quot;

