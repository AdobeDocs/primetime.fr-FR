---
seo-title: Présentation
title: Présentation
uuid: 2bbf0aa1-df35-429d-84df-db357fa53e47
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Présentation {#overview}

Pour obtenir une licence, les clients forment une requête à partir des métadonnées incorporées dans le contenu assemblé, puis envoient cette requête au serveur de licences. Le serveur de licences utilise les informations extraites des métadonnées de contenu pour générer une licence.

Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de requête est &quot;URL du serveur de licence dans les métadonnées&quot; + &quot; [!DNL /flashaccess/license/v4]&quot;. Si le protocole version 3 est le maximum pris en charge par le client ou le serveur, les clients DRM Primetime envoient alors des demandes d’authentification à &quot;URL du serveur de licences dans les métadonnées&quot; + &quot; [!DNL /flashaccess/license/v3]&quot;. Sinon, les demandes d’authentification sont envoyées à &quot;URL du serveur de licences dans les métadonnées&quot; + &quot; [!DNL /flashaccess/license/v1]&quot;

Un périphérique peut avoir plusieurs licences pour le même contenu (même ID de licence), mais ne peut avoir qu’une seule licence pour un ID de licence et un ID de stratégie DRM spécifiques. S’il reçoit une licence avec un ID de licence /ID de stratégie, la nouvelle licence ne remplace l’ancienne que si la date d’émission de la nouvelle licence est postérieure à la date d’émission de la licence existante. Cette logique est utilisée pour traiter les licences incorporées dans le contenu. Il n’est donc pas recommandé d’incorporer plusieurs licences avec le même ID de stratégie DRM dans un fragment de contenu. La même logique s’applique aux licences transmises au client par le biais de l’API `DRMManager.storeVoucher()` ActionScript3 ; si le client possède déjà une licence avec une date de publication ultérieure, la licence fournie peut être ignorée.

## Classes de traitement des demandes de licence {#section_190E3BEF316C4B09ACC21E4C2BAC5C75}

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler` - Il s&#39;agit de la classe du gestionnaire de demande de licence. Il lit et analyse les demandes de licence. Sa `getRequests()` méthode renvoie un d’ `LicenseRequestMessage` objets.
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage` - Il s&#39;agit de la classe de message de demande. L’appelant doit effectuer une itération sur le `LicenseRequestMessage` renvoyé par `getRequests()`, et pour chaque requête, générer une licence ou définir un code d’erreur. Appelez `LicenseRequestMessage.getContentInfo()` pour obtenir des informations extraites des métadonnées de contenu, y compris l’ID de contenu, l’ID de licence et les stratégies DRM.

Les licences et les erreurs sont envoyées au moment où la `LicenseHandler.close()` méthode est appelée.

Pour plus d’informations, consultez la documentation [de référence de l’API](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html) DRM Server.
