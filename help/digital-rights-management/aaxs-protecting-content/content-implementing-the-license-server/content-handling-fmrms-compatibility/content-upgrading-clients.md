---
seo-title: Mise à niveau des clients
title: Mise à niveau des clients
uuid: 9c9bc7da-2a97-4659-945a-554d778d30a3
translation-type: tm+mt
source-git-commit: 5cf90a75d8805fb64d7d145722ad10a1ce77a14d

---


# Mise à niveau des clients{#upgrading-clients}

Si un client FMRMS 1.x contacte un serveur Adobe Access, le serveur doit demander au client de procéder à la mise à niveau.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* L’URL de requête est &quot;URL de *base à partir du contenu* 1.x&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

   Contrairement aux autres gestionnaires de requêtes Adobe Access, ce gestionnaire ne permet pas d’accéder à des informations de requête ni de définir des données de réponse. Créez une instance de la `FMRMSv1RequestHandler`, puis appelez `close()`