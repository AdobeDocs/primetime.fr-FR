---
seo-title: Gestion des demandes d'enregistrement de domaine
title: Gestion des demandes d'enregistrement de domaine
uuid: e0cef9c4-b2d1-4bec-8dce-50452bc826fb
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gestion des demandes d&#39;enregistrement de domaine{#handling-domain-registration-requests}

Si les métadonnées DRM indiquent que l’enregistrement du domaine est nécessaire pour lire le contenu, l’application cliente doit appeler l’API ActionScript DRMManager.addToDeviceGroup() ou l’API iOS joinLicenseDomain(). Si le client n’est pas encore enregistré sur le serveur de domaine spécifié (ou si l’application oblige à un nouveau regroupement), une demande d’enregistrement de domaine est envoyée. Le serveur de domaine détermine si le client est autorisé à rejoindre un domaine et envoie au client une ou plusieurs informations d’identification de domaine.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de requête est &quot;URL du serveur de domaine dans les métadonnées : + &quot;/flashaccess/domain/v4&quot;. Dans le cas contraire, l’URL de requête est l’URL du serveur de domaine dans les métadonnées &quot; + &quot;/flashaccess/domain/v3&quot;

Lors de l’initialisation de `DomainRegistrationHandler`, l’URL du serveur de domaine doit être spécifiée. Cette URL sera incluse dans les jetons de domaine émis par le gestionnaire pour indiquer le serveur de domaine qui a émis le jeton. L’URL doit correspondre à l’URL du serveur de domaine spécifiée dans toute stratégie qui requiert l’enregistrement du domaine auprès du serveur.

Pour déterminer si le client est autorisé à rejoindre le domaine, le serveur peut examiner les informations de l’ordinateur et de l’utilisateur dans la requête. Voir [Utilisation d’identifiants](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-using-machine-ids.md) d’ordinateur pour plus d’informations sur la manière d’identifier et de comptabiliser les machines qui rejoignent le domaine. Le serveur peut également déterminer le domaine auquel le client est autorisé à se joindre. Notez qu’un client ne peut être membre que d’un domaine par URL de serveur de domaine. Si l’ordinateur dispose déjà d’un jeton de domaine pour cette URL de serveur de domaine, la demande d’enregistrement de domaine inclura le nom de domaine actuel ( `getRequestDomainName()`). Dans le cas d’une demande de reconnexion, le serveur de domaine doit renvoyer l’ensemble actuel d’informations d’identification de domaine pour ce domaine ou renvoyer une erreur (le serveur de domaine peut ne pas renvoyer les informations d’identification de domaine pour un autre domaine).

Si le serveur de domaine nécessite une authentification pour rejoindre un domaine, la requête doit contenir un jeton d’authentification. Tout comme pour une demande de licence, l’enregistrement de domaine peut nécessiter un nom d’utilisateur/mot de passe ou une authentification personnalisée. Voir Authentification [des](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-authentication/content-user-authentication.md) utilisateurs pour en savoir plus sur la gestion des jetons d’authentification.

Le serveur de domaine est responsable du stockage et de la gestion des clés de domaine associées à chaque domaine. Lorsqu’une nouvelle paire de clés doit être générée pour un domaine (premier enregistrement de domaine pour le domaine), appelez `generateDomainCredential``(String, int, Principal, Date)`. Cette méthode génère une nouvelle paire de clés de domaine et un nouveau certificat de domaine. Le serveur de domaine doit stocker la clé privée et le certificat et fournir ces objets lors du traitement des demandes ultérieures pour ce domaine. Il est également possible de générer une nouvelle paire de clés pour un domaine afin de rouler sur les clés. Lorsque vous passez la souris sur les clés d’un domaine particulier, veillez à incrémenter également la version clé `generateDomainCredential` .

Chaque fois qu’un ordinateur s’enregistre dans le même domaine, la même clé privée de domaine et le même certificat doivent être utilisés. Appelez `addDomainCredential(DomainToken, PrivateKey)` pour renvoyer au client des informations d’identification de domaine existantes. S’il existe plusieurs informations d’identification de domaine pour le domaine en raison de la modification des clés de domaine, le serveur doit fournir des informations d’identification de domaine pour la clé de domaine actuelle et toutes les clés de domaine précédentes afin que le client puisse consommer des licences liées aux anciennes clés de domaine. Cela permet à une licence liée à un ancien jeton de domaine d’être déplacée vers un nouvel ordinateur enregistré et d’être toujours lisible.
