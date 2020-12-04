---
seo-title: Gérer les demandes d'enregistrement de domaine
title: Gérer les demandes d'enregistrement de domaine
uuid: d92db6c2-5a16-41ea-a1aa-541c59780678
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---


# Gérer les demandes d&#39;enregistrement de domaine {#handle-domain-registration-requests}

Si les métadonnées DRM indiquent que l’enregistrement de domaine est nécessaire pour lire le contenu, l’application cliente doit appeler l’API d’ActionScript `DRMManager.addToDeviceGroup()` ou l’API iOS `joinLicenseDomain()`. Si le client n’a pas encore été enregistré sur le serveur de domaine spécifié (ou si l’application oblige à un renvoi), une demande d’enregistrement de domaine est envoyée. Le serveur de domaines détermine si le client est autorisé à rejoindre un domaine et envoie au client une ou plusieurs informations d’identification de domaine.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* Si le client et le serveur prennent en charge le protocole version 5, l’URL de demande est &quot;Domain Server URL in metadata : + &quot; [!DNL /flashaccess/domain/v4]&quot;. Dans le cas contraire, l’URL de demande est l’URL du serveur de domaine dans les métadonnées&quot; + &quot; [!DNL /flashaccess/domain/v3]&quot;

Lorsque vous initialisez `DomainRegistrationHandler`, vous devez spécifier l’URL du serveur de domaine. Cette URL est ensuite incluse dans les jetons de domaine émis par le gestionnaire pour indiquer au serveur de domaine que le jeton a été émis. L’URL doit correspondre à l’URL du serveur de domaine spécifiée dans toute stratégie DRM qui requiert l’enregistrement du domaine auprès du serveur.

Pour déterminer si le client est autorisé à rejoindre le domaine, le serveur peut examiner les informations de l’ordinateur et de l’utilisateur dans la demande. Le serveur peut également déterminer le domaine auquel le client est autorisé à se joindre.

>[!NOTE]
>
>Un client ne peut être membre que d’un seul domaine par URL de serveur de domaine. Si l&#39;ordinateur dispose déjà d&#39;un jeton de domaine pour cette URL de serveur de domaine, la demande d&#39;enregistrement de domaine inclut le nom de domaine actuel ( `getRequestDomainName()`).

Pour une demande de reconnexion, le serveur de domaine doit renvoyer l’ensemble actuel d’informations d’identification de domaine pour ce domaine ou renvoyer une erreur. Le serveur de domaine ne peut pas renvoyer les informations d&#39;identification de domaine pour un autre domaine.

Voir [Utilisation d&#39;identifiants d&#39;ordinateur](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#use-machine-identifiers) pour plus d&#39;informations sur la manière d&#39;identifier et de comptabiliser les machines qui se joignent au domaine.

Si le serveur de domaine nécessite une authentification pour rejoindre un domaine, la demande doit contenir un jeton d’authentification. Tout comme pour une demande de licence, l’enregistrement de domaine peut nécessiter un nom d’utilisateur/mot de passe ou une authentification personnalisée.

Voir [Authentification des utilisateurs](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#user-authentication) pour plus d&#39;informations sur la gestion des jetons d&#39;authentification.

Le serveur de domaine est chargé de stocker et de gérer les clés de domaine associées à chaque domaine. Lorsqu&#39;une nouvelle paire de clés doit être générée pour un domaine (le premier enregistrement de domaine pour le domaine), vous devez appeler `generateDomainCredential(String, int, Principal, Date)`. Cette méthode génère une nouvelle paire de clés de domaine et un nouveau certificat de domaine. Le serveur de domaine doit stocker la clé privée et le certificat et fournir ces objets lors du traitement des demandes suivantes pour ce domaine. Il est également possible de générer une nouvelle paire de clés pour un domaine afin de rouler sur les clés. Lorsque vous placez le pointeur de la souris sur les clés d&#39;un domaine particulier, veillez à incrémenter la version de clé dans `generateDomainCredential`.

Chaque fois qu’un ordinateur s’enregistre sur le même domaine, la même clé privée de domaine et le même certificat doivent être utilisés. Appelez `addDomainCredential(DomainToken, PrivateKey)` pour renvoyer au client des informations d’identification de domaine existantes. S’il existe plusieurs informations d’identification de domaine pour le domaine en raison de la modification des clés de domaine, le serveur doit fournir les informations d’identification de domaine pour la clé de domaine actuelle et toutes les clés de domaine précédentes afin que le client puisse utiliser des licences liées à des clés de domaine plus anciennes. Cela permet de déplacer une licence liée à un ancien jeton de domaine sur un nouvel ordinateur enregistré et de pouvoir continuer à être lue.
