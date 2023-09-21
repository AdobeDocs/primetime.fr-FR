---
title: Gestion des demandes d’enregistrement de domaine
description: Gestion des demandes d’enregistrement de domaine
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Gestion des demandes d’enregistrement de domaine {#handle-domain-registration-requests}

Si les métadonnées DRM indiquent que l’enregistrement du domaine est nécessaire pour lire le contenu, l’application cliente doit appeler la fonction `DRMManager.addToDeviceGroup()` API ActionScript ou `joinLicenseDomain()` API iOS. Si le client ne s’est pas encore enregistré auprès du serveur de domaine spécifié (ou si l’application force un retour), une demande d’enregistrement de domaine est envoyée. Le serveur de domaine détermine si le client est autorisé à rejoindre un domaine et transmet au client une ou plusieurs informations d’identification de domaine.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* La classe de message de requête est `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de demande est &quot;Domain Server URL in metadata: + &quot; [!DNL /flashaccess/domain/v4]&quot;. Dans le cas contraire, l’URL de demande est Domain Server URL in metadata&quot; + &quot; [!DNL /flashaccess/domain/v3]&quot;

Lorsque vous initialisez la variable `DomainRegistrationHandler`, vous devez spécifier l’URL du serveur de domaine. Cette URL est ensuite incluse dans les jetons de domaine émis par le gestionnaire pour indiquer au serveur de domaine que le jeton a été émis. L’URL doit correspondre à l’URL du serveur de domaine spécifiée dans toute stratégie DRM nécessitant l’enregistrement du domaine auprès du serveur.

Pour déterminer si le client est autorisé à rejoindre le domaine, le serveur peut examiner les informations sur l’ordinateur et l’utilisateur dans la requête. Le serveur peut également déterminer le domaine auquel le client est autorisé à se joindre.

>[!NOTE]
>
>Un client ne peut être membre que d’un seul domaine par URL de serveur de domaine. Si l’ordinateur dispose déjà d’un jeton de domaine pour l’URL de ce serveur de domaine, la demande d’enregistrement de domaine inclut le nom de domaine actuel ( `getRequestDomainName()`).

Pour une demande de rejointure, le serveur de domaine doit renvoyer l’ensemble actuel des informations d’identification de domaine pour ce domaine ou renvoyer une erreur. Le serveur de domaine ne peut pas renvoyer les informations d’identification de domaine pour un autre domaine.

Voir [Utilisation des identifiants de machine](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#use-machine-identifiers) pour plus d’informations sur la manière d’identifier et de compter les machines qui rejoignent le domaine.

Si le serveur de domaine requiert une authentification pour rejoindre un domaine, la requête doit contenir un jeton d’authentification. Tout comme pour une demande de licence, l’enregistrement de domaine peut nécessiter une authentification personnalisée ou par nom d’utilisateur/mot de passe.

Voir [Authentification de l’utilisateur](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#user-authentication) pour plus d’informations sur la gestion des jetons d’authentification.

Le serveur de domaine est responsable du stockage et de la gestion des clés de domaine associées à chaque domaine. Lorsqu’une nouvelle paire de clés doit être générée pour un domaine (le premier enregistrement de domaine pour le domaine), vous devez appeler `generateDomainCredential(String, int, Principal, Date)`. Cette méthode génère une nouvelle paire de clés de domaine et un nouveau certificat de domaine. Le serveur de domaine doit stocker la clé privée et le certificat et fournir ces objets lors du traitement des demandes ultérieures pour ce domaine. Il est également possible de générer une nouvelle paire de clés pour un domaine afin de rouler sur les clés. Lorsque vous placez le pointeur de la souris sur les clés d’un domaine particulier, veillez à incrémenter la version clé dans `generateDomainCredential`.

Chaque fois qu’une machine s’enregistre avec le même domaine, la même clé privée de domaine et le même certificat doivent être utilisés. Appeler `addDomainCredential(DomainToken, PrivateKey)` pour renvoyer des informations d’identification de domaine existantes au client. S’il existe plusieurs informations d’identification de domaine pour le domaine, car les clés de domaine ont été modifiées, le serveur doit fournir les informations d’identification de domaine pour la clé de domaine actuelle et toutes les clés de domaine précédentes, de sorte que le client puisse utiliser des licences liées à des clés de domaine plus anciennes. Cela permet de déplacer une licence liée à un ancien jeton de domaine vers un nouvel ordinateur enregistré et de pouvoir la lire.
