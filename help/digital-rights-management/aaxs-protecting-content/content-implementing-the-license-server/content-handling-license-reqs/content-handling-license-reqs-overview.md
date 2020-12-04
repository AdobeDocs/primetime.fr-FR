---
seo-title: Présentation
title: Présentation
uuid: d3bfa65b-2360-4843-b59e-71451fa62a2c
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# Présentation{#overview}

Pour demander une licence, le client envoie les métadonnées qui ont été incorporées dans le contenu au cours de l’assemblage. Le serveur de licences utilise les informations contenues dans les métadonnées de contenu pour générer une licence.

`LicenseHandler` lit une demande de licence et analyse la demande. `LicenseHandler`s’étend  `BatchHandlerBase` aux demandes de licence par lot, bien que cette fonction ne soit actuellement pas prise en charge par les clients d’Adobe Access. La méthode `getRequests()` renvoie une Liste d&#39;objets `LicenseRequestMessage`. L&#39;appelant doit effectuer une itération dans `LicenseRequestMessages` et pour chaque demande, générer une licence ou définir un code d&#39;erreur (voir la documentation de référence de l&#39;API `LicenseRequestMessage` pour plus de détails). Pour chaque demande de licence, le serveur détermine s’il délivrera une licence. Appelez `LicenseRequestMessage.getContentInfo()` pour obtenir des informations extraites à partir des métadonnées de contenu, y compris l’ID de contenu, l’ID de licence et les stratégies.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de demande est &quot;URL du serveur de licence dans les métadonnées : + &quot;/flashaccess/license/v4&quot;. Si le protocole version 3 est le maximum pris en charge par le client ou le serveur, les clients Adobe Access envoient des demandes d&#39;authentification à &quot;License Server URL in metadata&quot; + &quot;/flashaccess/license/v3&quot;. Sinon, les demandes d’authentification sont envoyées à &quot;l’URL du serveur de licence dans les métadonnées&quot; + &quot;/flashaccess/license/v1&quot;

Si une erreur se produit lors de l’analyse de la requête, un `HandlerParsingException` est généré. Cette exception contient des informations d’erreur à renvoyer au client. Pour récupérer les informations d&#39;erreur, appelez `HandlerParsingException.getErrorData()`. Si une erreur se produit lors de la génération d&#39;une licence, car les exigences de la stratégie n&#39;ont pas été satisfaites, un `PolicyEvaluationException` est généré. Cette exception inclut également `ErrorData` à renvoyer au client. Consultez la documentation de l’API pour `LicenseRequestMessage.generateLicense()` pour plus d’informations sur la manière dont les stratégies sont évaluées lors de la génération de la licence.

Les licences et les erreurs sont envoyées à un moment où `LicenseHandler.close()` est appelé.

Un périphérique peut posséder plusieurs licences pour le même contenu (même ID de licence), mais ne peut posséder qu’une seule licence pour un ID de licence et un ID de stratégie particuliers. S&#39;il reçoit une licence avec un ID de licence/ID de stratégie duplicata, la nouvelle licence ne remplacera l&#39;ancienne que si la date d&#39;émission de la nouvelle licence est postérieure à la date d&#39;émission de la licence existante. Cette logique est utilisée pour traiter les licences incorporées dans du contenu. Il n’est donc pas recommandé d’incorporer plusieurs licences avec le même ID de stratégie dans un fragment de contenu. La même logique s&#39;applique aux licences transmises au client par le biais de l&#39;API `DRMManager.storeVoucher()` ActionScript3 ; si le client possède déjà une licence avec une date de délivrance ultérieure, la licence fournie peut être ignorée.
