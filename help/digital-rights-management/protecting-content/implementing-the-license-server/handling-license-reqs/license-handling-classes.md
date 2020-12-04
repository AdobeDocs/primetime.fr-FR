---
seo-title: Présentation
title: Présentation
uuid: 2bbf0aa1-df35-429d-84df-db357fa53e47
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# Aperçu {#overview}

Pour obtenir une licence, les clients formulent une requête à partir des métadonnées incorporées dans le contenu assemblé, puis envoient cette requête au serveur de licences. Le serveur de licences utilise des informations extraites des métadonnées de contenu pour générer une licence.

Si le client et le serveur prennent tous deux en charge la version 5 du protocole, l’URL de demande est &quot;URL du serveur de licence dans les métadonnées&quot; + &quot; [!DNL /flashaccess/license/v4]&quot;. Si le protocole version 3 est le maximum pris en charge par le client ou le serveur, les clients DRM Primetime envoient alors des demandes d&#39;authentification à &quot;License Server URL in metadata&quot; + &quot; [!DNL /flashaccess/license/v3]&quot;. Sinon, les demandes d&#39;authentification sont envoyées à &quot;l&#39;URL du serveur de licences dans les métadonnées&quot; + &quot; [!DNL /flashaccess/license/v1]&quot;

Un périphérique peut posséder plusieurs licences pour le même contenu (même ID de licence), mais ne peut posséder qu’une seule licence pour un ID de licence et un ID de stratégie DRM spécifiques. S&#39;il reçoit une licence avec un ID de licence/ID de stratégie duplicata, la nouvelle licence ne remplace l&#39;ancienne que si la date d&#39;émission de la nouvelle licence est postérieure à la date d&#39;émission de la licence existante. Cette logique est utilisée pour traiter les licences incorporées dans le contenu. Il n’est donc pas recommandé d’incorporer plusieurs licences avec le même ID de stratégie DRM dans un fragment de contenu. La même logique s&#39;applique aux licences transmises au client par le biais de l&#39;API `DRMManager.storeVoucher()` ActionScript3 ; si le client possède déjà une licence avec une date de délivrance ultérieure, la licence fournie peut être ignorée.

## Classes de traitement des demandes de licence {#section_190E3BEF316C4B09ACC21E4C2BAC5C75}

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler` - Il s&#39;agit de la classe du gestionnaire de demandes de licence. Il lit et analyse les demandes de licence. Sa méthode `getRequests()` renvoie une liste d&#39;objets `LicenseRequestMessage`.
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage` - Il s&#39;agit de la classe de message de demande. L’appelant doit effectuer une itération sur la liste `LicenseRequestMessage` renvoyée par `getRequests()` et, pour chaque requête, générer une licence ou définir un code d’erreur. Appelez `LicenseRequestMessage.getContentInfo()` pour obtenir des informations extraites à partir des métadonnées de contenu, y compris l’ID de contenu, l’ID de licence et les stratégies DRM.

Les licences et les erreurs sont envoyées simultanément lorsque la méthode `LicenseHandler.close()` est appelée.

Pour plus d’informations, consultez la [documentation de référence de l’API du serveur DRM](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html).
