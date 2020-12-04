---
seo-title: Gestion des demandes de désenregistrement de domaine
title: Gestion des demandes de désenregistrement de domaine
uuid: 6f056b2b-374d-4e4d-926a-68605b2c923b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Gestion des demandes de désinscription de domaine{#handling-domain-de-registration-requests}

Si l’application cliente doit quitter un domaine, elle appelle l’API d’ActionScript `DRMManager.removeFromDeviceGroup()`ou l’API iOS `leaveLicenseDomain()` pour lancer le processus de désenregistrement de domaine. Le désenregistrement des domaines est un processus en deux phases. Le client envoie d’abord une demande de prévisualisation de désinscription. Le serveur de domaines examine la demande et détermine si le client est autorisé à quitter le domaine (une erreur peut être renvoyée si l’ordinateur ne fait pas actuellement partie du domaine). En cas de réponse positive, le client supprime ses informations d’identification de domaine et toutes les licences délivrées à ce domaine, puis envoie une demande de désinscription.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Si le client et le serveur prennent en charge le protocole version 5, l’URL de demande est &quot;Domain Server URL in metadata : + &quot;/flashaccess/dereg/v4&quot;. Dans le cas contraire, l’URL de demande est l’URL du serveur de domaine dans les métadonnées &quot; + &quot;/flashaccess/dereg/v3&quot;

Lors du traitement des demandes de désinscription de domaine, le serveur utilise `getRequestPhase()` pour déterminer si le client est en phase de prévisualisation ou de désinscription. Au cours de la phase de prévisualisation, le serveur de domaine examine la demande et détermine si le client est autorisé à quitter le domaine (la demande peut être refusée, par exemple, si l’ordinateur ne fait pas actuellement partie du domaine). Lors de la phase de désenregistrement, le serveur enregistre le fait que l&#39;ordinateur a quitté le domaine. Il est vivement recommandé au serveur d’évaluer la même logique dans la demande de prévisualisation que dans la demande de désinscription réelle afin de minimiser les risques d’échec de la deuxième phase.
