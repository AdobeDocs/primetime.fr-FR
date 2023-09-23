---
title: Mise à niveau des clients
description: Mise à niveau des clients
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---

# Mise à niveau des clients{#upgrading-clients}

Si un client FMRMS 1.x contacte un serveur Adobe Access, le serveur doit inviter le client à effectuer la mise à niveau.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* L’URL de demande est &quot;*URL de base du contenu 1.x*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

  Contrairement à d’autres gestionnaires de requêtes d’accès aux Adobes, ce gestionnaire ne permet pas d’accéder aux informations de requête ni ne nécessite la définition de données de réponse. Créez une instance de la fonction `FMRMSv1RequestHandler`, puis appelez `close()`
