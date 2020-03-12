---
seo-title: Présentation
title: Présentation
uuid: 870c32f5-1119-4fec-abed-25e51dd1ebe3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation{#overview}

La méthode générale de traitement des requêtes consiste à créer un gestionnaire, analyser la requête, définir les données de réponse ou le code d’erreur, puis fermer le gestionnaire.

La classe de base utilisée pour gérer l’interaction requête/réponse unique est `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Une instance de la `HandlerConfiguration` classe est utilisée pour initialiser le gestionnaire. `HandlerConfiguration` stocke les informations de configuration du serveur, notamment les informations d’identification du transport, la tolérance d’horodatage, les  de mise à jour de stratégie et les de révocation. Le gestionnaire lit les données de requête et analyse la requête dans une instance de `RequestMessageBase`. L’appelant peut examiner les informations contenues dans la requête et décider s’il renvoie une erreur ou une réponse positive (les sous-classes de `RequestMessageBase` fournissent une méthode de définition des données de réponse).

Si la requête aboutit, définissez les données de réponse ; invoquez sinon `RequestMessageBase.setErrorData()` en cas d’échec. Mettez toujours fin à l’implémentation en appelant la `close()` méthode (il est recommandé `close()` d’être appelé dans le `finally` bloc d’une `try` instruction). Consultez la documentation de référence `MessageHandlerBase` API pour obtenir un exemple d’appel du gestionnaire.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Le code d’état HTTP 200 (OK) doit être envoyé en réponse à toutes les requêtes traitées par le gestionnaire. Si le gestionnaire n’a pas pu être créé en raison d’une erreur du serveur, le serveur peut répondre avec un autre code d’état, tel que 500 (Erreur interne du serveur).

Le client utilise l’URL du serveur de licences spécifiée au moment du pack comme URL de base pour toutes les requêtes envoyées au serveur de licences. Par exemple, si l’URL du serveur est spécifiée comme &quot;<span></span>https://licenseserver.com/path&quot;, le client envoie des requêtes à &quot;<span></span>https://licenseserver.com/path/flashaccess/...&quot;. Consultez les sections suivantes pour plus d’informations sur le chemin spécifique utilisé pour chaque type de requête. Lors de la mise en oeuvre de votre serveur de licences, veillez à ce que le serveur réponde aux chemins d’accès requis pour chaque type de requête.

Une demande de licence peut contenir un jeton d’authentification. Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la requête peut contenir une `AuthenticationToken` générée par le `AuthenticationHandler`, et le SDK s’assurera que le jeton est valide avant d’émettre une licence.
