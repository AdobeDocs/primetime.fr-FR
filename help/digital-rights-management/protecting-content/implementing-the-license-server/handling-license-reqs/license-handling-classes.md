---
title: Présentation
description: Présentation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Présentation {#overview}

Pour obtenir une licence, les clients forment une demande à partir des métadonnées intégrées au contenu empaqueté, puis envoient cette demande au serveur de licences. Le serveur de licences utilise des informations extraites des métadonnées de contenu pour générer une licence.

Si le client et le serveur prennent tous deux en charge le protocole version 5, l’URL de la demande est &quot;URL du serveur de licences dans les métadonnées&quot; + &quot; [!DNL /flashaccess/license/v4]&quot;. Si le protocole version 3 est le maximum pris en charge par le client ou le serveur, les clients DRM Primetime envoient alors des demandes d’authentification à &quot;URL du serveur de licences dans les métadonnées&quot; + &quot; [!DNL /flashaccess/license/v3]&quot;. Sinon, les demandes d’authentification sont envoyées à &quot;URL du serveur de licences dans les métadonnées&quot; + &quot; [!DNL /flashaccess/license/v1]&quot;

Un appareil peut posséder plusieurs licences pour le même contenu (même ID de licence), mais ne peut avoir qu’une seule licence pour un ID de licence et un ID de stratégie DRM spécifiques. S’il reçoit une licence avec un ID de licence/stratégie en double, la nouvelle licence remplace l’ancienne uniquement si la date d’émission de la nouvelle licence est postérieure à la date d’émission de la licence existante. Cette logique est utilisée pour traiter les licences incorporées dans le contenu. Il n’est donc pas recommandé d’incorporer plusieurs licences avec le même identifiant de stratégie DRM dans un bloc de contenu. La même logique s’applique aux licences transmises au client par l’intermédiaire du `DRMManager.storeVoucher()` API ActionScript3 ; si le client possède déjà une licence avec une date de publication ultérieure, la licence fournie peut être ignorée.

## Classes de gestion des demandes de licence {#section_190E3BEF316C4B09ACC21E4C2BAC5C75}

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler` - Il s’agit de la classe du gestionnaire de demandes de licence. Il lit et analyse les demandes de licence. Son `getRequests()` renvoie une liste de `LicenseRequestMessage` objets.
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage` - Il s’agit de la classe de message de requête. L’appelant doit effectuer une itération sur la variable `LicenseRequestMessage` liste renvoyée par `getRequests()`, et pour chaque demande, générez une licence ou définissez un code d’erreur. Appeler `LicenseRequestMessage.getContentInfo()` pour obtenir des informations extraites des métadonnées de contenu, y compris l’ID de contenu, l’ID de licence et les stratégies DRM.

Les licences et les erreurs sont envoyées simultanément lorsque la variable `LicenseHandler.close()` est appelée.

Voir [Documentation de référence de l’API du serveur DRM](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html) pour plus d’informations.
