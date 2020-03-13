---
seo-title: Gestion des demandes de désenregistrement de domaine
title: Gestion des demandes de désenregistrement de domaine
uuid: 6f056b2b-374d-4e4d-926a-68605b2c923b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gestion des demandes de désenregistrement de domaine{#handling-domain-de-registration-requests}

Si l’application cliente doit quitter un domaine, elle appelle l’API `DRMManager.removeFromDeviceGroup()`ActionScript ou l’API `leaveLicenseDomain()` iOS pour lancer le processus de désenregistrement de domaine. Le désenregistrement de domaine est un processus en deux phases. Le client envoie d’abord une demande de  de désinscription. Le serveur de domaine examine la requête et détermine si le client est autorisé à quitter le domaine (une erreur peut être renvoyée si l’ordinateur ne fait pas actuellement partie du domaine). En cas de réponse positive, le client supprime ses informations d’identification de domaine et toutes les licences délivrées à ce domaine, puis envoie une demande de désenregistrement.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de requête est &quot;URL du serveur de domaine dans les métadonnées : + &quot;/flashaccess/dereg/v4&quot;. Dans le cas contraire, l’URL de requête est l’URL du serveur de domaine dans les métadonnées &quot; + &quot;/flashaccess/dereg/v3&quot;

Lors du traitement des demandes de désenregistrement de domaine, le serveur détermine `getRequestPhase()` si le client est dans la phase de  ou de désenregistrement du domaine. Au cours de la phase , le serveur de domaine examine la requête et détermine si le client est autorisé à quitter le domaine (la requête peut être refusée, par exemple, si l’ordinateur ne fait pas actuellement partie du domaine). Lors de la phase de désenregistrement, le serveur enregistre le fait que l&#39;ordinateur a quitté le domaine. Il est vivement recommandé au serveur d’évaluer la même logique dans la demande de  du que dans la demande de désinscription réelle afin de minimiser les risques d’échec de la deuxième phase.
