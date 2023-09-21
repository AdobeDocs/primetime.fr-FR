---
title: Gestion des demandes de désenregistrement de domaine
description: Gestion des demandes de désenregistrement de domaine
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Gestion des demandes de désenregistrement de domaine {#handle-domain-de-registration-requests}

Si l’application cliente doit quitter un domaine, elle appelle la variable `DRMManager.removeFromDeviceGroup()`API d’ActionScript ou `leaveLicenseDomain()` API iOS pour lancer le processus de désinscription de domaine. La désinscription du domaine est un processus en deux phases. Le client envoie d’abord une demande d’aperçu de désinscription. Le serveur de domaine examine la demande et détermine si le client est autorisé à quitter le domaine. Une erreur peut être renvoyée si la machine ne fait pas actuellement partie du domaine. En cas de réponse réussie, le client supprime ses informations d’identification de domaine et toutes les licences qui ont été délivrées à ce domaine. Il envoie ensuite une demande de désinscription.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* La classe de message de requête est `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Si le client et le serveur prennent en charge la version 5 du protocole, l’URL de demande est &quot;Domain Server URL in metadata: + &quot; [!DNL /flashaccess/dereg/v4]&quot;. Dans le cas contraire, l’URL de demande est Domain Server URL in metadata&quot; + &quot; [!DNL /flashaccess/dereg/v3]&quot;

Lors du traitement des demandes de désinscription de domaine, le serveur utilise `getRequestPhase()` pour déterminer si le client est en phase de prévisualisation ou de désinscription. Lors de la phase de prévisualisation, le serveur de domaine examine la demande et détermine si le client est autorisé à quitter le domaine car la demande peut être refusée ; par exemple, la demande peut être refusée si la machine ne fait pas actuellement partie du domaine. Lors de la phase de désinscription, le serveur enregistre le fait que la machine a quitté le domaine. Le serveur est vivement recommandé d’évaluer la même logique dans la requête de prévisualisation que dans la requête de désinscription réelle afin de minimiser les risques d’échec de la deuxième phase.
