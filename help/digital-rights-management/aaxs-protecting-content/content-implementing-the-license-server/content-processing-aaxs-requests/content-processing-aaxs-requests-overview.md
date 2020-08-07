---
seo-title: Présentation
title: Présentation
uuid: 870c32f5-1119-4fec-abed-25e51dd1ebe3
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---


# Présentation{#overview}

La méthode générale de traitement des requêtes consiste à créer un gestionnaire, analyser la requête, définir les données de réponse ou le code d’erreur et fermer le gestionnaire.

La classe de base utilisée pour gérer l&#39;interaction requête/réponse unique est `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Une instance de la `HandlerConfiguration` classe est utilisée pour initialiser le gestionnaire. `HandlerConfiguration` stocke les informations de configuration du serveur, notamment les informations d&#39;identification de transport, la tolérance d&#39;horodatage, les listes de mise à jour de stratégie et les listes de révocation. Le gestionnaire lit les données de demande et analyse la demande dans une instance de `RequestMessageBase`. L’appelant peut examiner les informations contenues dans la requête et décider s’il doit renvoyer une erreur ou une réponse positive (les sous-classes de `RequestMessageBase` fournissent une méthode de définition des données de réponse).

Si la demande aboutit, définissez les données de la réponse ; dans le cas contraire, appelez `RequestMessageBase.setErrorData()` en cas d’échec. Mettez toujours fin à l’implémentation en appelant la `close()` méthode (il est recommandé d’ `close()` appeler dans le `finally` bloc d’une `try` instruction). Consultez la documentation de référence sur les `MessageHandlerBase` API pour un exemple d’appel du gestionnaire.

>[!NOTE]
>
>Le code d’état HTTP 200 (OK) doit être envoyé en réponse à toutes les requêtes traitées par le gestionnaire. Si le gestionnaire n&#39;a pas pu être créé en raison d&#39;une erreur du serveur, le serveur peut répondre avec un autre code d&#39;état, tel que 500 (Erreur interne du serveur).

Le client utilise l’URL du serveur de licences spécifiée au moment du pack comme URL de base pour toutes les requêtes envoyées au serveur de licences. Par exemple, si l’URL du serveur est spécifiée comme &quot;<span></span>https://licenseserver.com/path&quot;, le client envoie des requêtes à &quot;<span></span>https://licenseserver.com/path/flashaccess/...&quot;. Consultez les sections suivantes pour en savoir plus sur le chemin d’accès spécifique utilisé pour chaque type de requête. Lors de la mise en oeuvre de votre serveur de licences, veillez à ce qu’il réponde aux chemins d’accès requis pour chaque type de requête.

Une demande de licence peut contenir un jeton d’authentification. Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la demande peut contenir une `AuthenticationToken` générée par le `AuthenticationHandler`SDK et le jeton s’assurera qu’il est valide avant d’émettre une licence.
