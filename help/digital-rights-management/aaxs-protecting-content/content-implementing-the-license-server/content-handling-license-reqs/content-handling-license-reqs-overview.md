---
title: Présentation
description: Présentation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Présentation{#overview}

Pour demander une licence, le client envoie les métadonnées qui ont été incorporées dans le contenu lors du conditionnement. Le serveur de licences utilise les informations contenues dans les métadonnées de contenu pour générer une licence.

La variable `LicenseHandler` lit une demande de licence et analyse la demande. `LicenseHandler`étend `BatchHandlerBase` pour répondre aux demandes de licence par lots, bien que cette fonctionnalité ne soit actuellement pas prise en charge par les clients Adobe Access. La variable `getRequests()` renvoie une liste de `LicenseRequestMessage` objets. L’appelant doit effectuer une itération sur la variable `LicenseRequestMessages`, et pour chaque demande, générez une licence ou définissez un code d’erreur (voir la section `LicenseRequestMessage` Documentation de référence de l’API pour plus d’informations). Pour chaque demande de licence, le serveur détermine s’il va émettre une licence. Appeler `LicenseRequestMessage.getContentInfo()` pour obtenir des informations extraites des métadonnées de contenu, y compris l’ID de contenu, l’ID de licence et les stratégies.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`
* La classe de message de requête est `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de demande est &quot;URL du serveur de licences dans les métadonnées : + &quot;/flashaccess/license/v4&quot;. Si le protocole version 3 est le maximum pris en charge par le client ou le serveur, les clients Adobe Access envoient des demandes d’authentification à &quot;URL du serveur de licences dans les métadonnées&quot; + &quot;/flashaccess/license/v3&quot;. Sinon, les demandes d’authentification sont envoyées à &quot;URL du serveur de licences dans les métadonnées&quot; + &quot;/flashaccess/license/v1&quot;

Si une erreur se produit lors de l’analyse de la requête, une `HandlerParsingException` est généré. Cette exception contient des informations d’erreur à renvoyer au client. Pour récupérer les informations d’erreur, appelez `HandlerParsingException.getErrorData()`. Si une erreur se produit lors de la génération d’une licence car les exigences de la stratégie n’ont pas été satisfaites, une `PolicyEvaluationException` est généré. Cette exception inclut également `ErrorData` à renvoyer au client. Consultez la documentation de l’API pour `LicenseRequestMessage.generateLicense()` pour plus d’informations sur la manière dont les stratégies sont évaluées lors de la génération de la licence.

Les licences et les erreurs sont envoyées simultanément lorsque `LicenseHandler.close()` est appelée.

Un appareil peut posséder plusieurs licences pour le même contenu (même ID de licence), mais ne peut avoir qu’une seule licence pour un ID de licence et un ID de stratégie spécifiques. S’il reçoit une licence comportant un ID de licence/stratégie en double, la nouvelle licence ne remplacera l’ancienne que si la date d’émission de la nouvelle licence est postérieure à la date d’émission de la licence existante. Cette logique est utilisée pour traiter les licences incorporées dans du contenu. Il n’est donc pas recommandé d’incorporer plusieurs licences avec le même ID de stratégie dans un bloc de contenu. La même logique s’applique aux licences transmises au client par l’intermédiaire du `DRMManager.storeVoucher()` API ActionScript3 ; si le client possède déjà une licence avec une date de publication ultérieure, la licence fournie peut être ignorée.
