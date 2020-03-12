---
seo-title: Présentation
title: Présentation
uuid: d3bfa65b-2360-4843-b59e-71451fa62a2c
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Présentation{#overview}

Pour demander une licence, le client envoie les métadonnées qui ont été incorporées dans le contenu au cours de l’assemblage. Le serveur de licences utilise les informations contenues dans les métadonnées de contenu pour générer une licence.

Il `LicenseHandler` lit une demande de licence et analyse la demande. `LicenseHandler`s’étend `BatchHandlerBase` aux demandes de licence par lot, bien que cette fonctionnalité ne soit actuellement pas prise en charge par les clients Adobe Access. La `getRequests()` méthode renvoie un  d’ `LicenseRequestMessage` objets. L’appelant doit effectuer une itération dans le `LicenseRequestMessages`, et pour chaque requête, générer une licence ou définir un code d’erreur (voir la documentation de référence `LicenseRequestMessage` API pour plus de détails). Pour chaque demande de licence, le serveur détermine s’il délivrera une licence. Appelez `LicenseRequestMessage.getContentInfo()` pour obtenir des informations extraites des métadonnées de contenu, y compris l’ID de contenu, l’ID de licence et les stratégies.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de requête est &quot;URL du serveur de licence dans les métadonnées : + &quot;/flashaccess/license/v4&quot;. Si le protocole version 3 est le maximum pris en charge par le client ou le serveur, les clients Adobe Access envoient des demandes d’authentification à &quot;URL du serveur de licences dans les métadonnées&quot; + &quot;/flashaccess/license/v3&quot;. Sinon, les demandes d’authentification sont envoyées à &quot;URL du serveur de licences dans les métadonnées&quot; + &quot;/flashaccess/license/v1&quot;

Si une erreur se produit lors de l’analyse de la requête, une erreur `HandlerParsingException` est générée. Cette exception contient des informations d’erreur à renvoyer au client. Pour récupérer les informations d’erreur, appelez `HandlerParsingException.getErrorData()`. Si une erreur se produit lors de la génération d’une licence car les conditions requises par la stratégie n’ont pas été satisfaites, une erreur `PolicyEvaluationException` est générée. Cette exception inclut également le renvoi `ErrorData` au client. Consultez la documentation de l’API `LicenseRequestMessage.generateLicense()` pour plus d’informations sur la manière dont les stratégies sont évaluées lors de la génération de la licence.

Les licences et les erreurs sont envoyées au moment de `LicenseHandler.close()` l’appel.

Un périphérique peut avoir plusieurs licences pour le même contenu (même ID de licence), mais ne peut avoir qu’une seule licence pour un ID de licence et un ID de stratégie spécifiques. S’il reçoit une licence avec un ID de licence /ID de stratégie, la nouvelle licence ne remplace l’ancienne que si la date de publication de la nouvelle licence est postérieure à la date de publication de la licence existante. Cette logique est utilisée pour traiter les licences incorporées dans le contenu. Il n’est donc pas recommandé d’incorporer plusieurs licences avec le même ID de stratégie dans un fragment de contenu. La même logique s’applique aux licences transmises au client par le biais de l’API `DRMManager.storeVoucher()` ActionScript3 ; si le client possède déjà une licence avec une date de publication ultérieure, la licence fournie peut être ignorée.
