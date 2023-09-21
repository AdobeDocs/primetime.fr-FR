---
title: Présentation
description: Présentation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Présentation{#overview}

La méthode générale de gestion des requêtes consiste à créer un gestionnaire, à analyser la requête, à définir les données de réponse ou le code d’erreur et à fermer le gestionnaire.

La classe de base utilisée pour gérer l’interaction requête/réponse unique est `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Une instance de la fonction `HandlerConfiguration` est utilisée pour initialiser le gestionnaire. `HandlerConfiguration` stocke les informations de configuration du serveur, notamment les informations d’identification du transport, la tolérance à l’horodatage, les listes de mise à jour de stratégie et les listes de révocation. Le gestionnaire lit les données de requête et analyse la requête dans une instance de `RequestMessageBase`. L’appelant peut examiner les informations de la requête et décider s’il doit renvoyer une erreur ou une réponse réussie (sous-classes de `RequestMessageBase` fournir une méthode pour définir les données de réponse).

Si la requête aboutit, définissez les données de réponse ; sinon appelez `RequestMessageBase.setErrorData()` en cas d’échec. Mettez toujours fin à l’implémentation en appelant la variable `close()` (il est recommandé d’utiliser la méthode `close()` être appelée dans la variable `finally` bloc d’un `try` ). Voir `MessageHandlerBase` Documentation de référence sur l’API pour obtenir un exemple d’appel du gestionnaire.

>[!NOTE]
>
>Le code d’état HTTP 200 (OK) doit être envoyé en réponse à toutes les requêtes traitées par le gestionnaire. Si le gestionnaire n’a pas pu être créé en raison d’une erreur du serveur, le serveur peut répondre avec un autre code d’état, tel que 500 (Erreur interne du serveur).

Le client utilise l’URL du serveur de licences spécifiée au moment du regroupement comme URL de base pour toutes les demandes envoyées au serveur de licences. Par exemple, si l’URL du serveur est spécifiée sous la forme &quot;ht&quot;<span></span>tps://licenseserver.com/path&quot;, le client enverra des requêtes à &quot;https&quot;<span></span>tps://licenseserver.com/path/flashaccess/...&quot;. Consultez les sections suivantes pour plus d’informations sur le chemin spécifique utilisé pour chaque type de requête. Lors de la mise en oeuvre de votre serveur de licences, assurez-vous que le serveur répond aux chemins requis pour chaque type de demande.

Une demande de licence peut contenir un jeton d’authentification. Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la requête peut contenir une `AuthenticationToken` généré par la variable `AuthenticationHandler`, et le SDK s’assure que le jeton est valide avant d’émettre une licence.
