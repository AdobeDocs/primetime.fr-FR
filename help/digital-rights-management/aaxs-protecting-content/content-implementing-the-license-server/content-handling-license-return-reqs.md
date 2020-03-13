---
seo-title: Gestion des demandes de retour de licence
title: Gestion des demandes de retour de licence
uuid: d184faea-88cb-44f3-a253-e5314d577f17
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gestion des demandes de retour de licence{#handling-license-return-requests}

Si l’application cliente doit renvoyer une licence, elle appelle l’API ActionScript DRMManager.returnVoucher() pour lancer le processus. Cette API peut fonctionner en mode de validation immédiate ou en mode de confirmationPremière. Si la valeur de la propriété immédiatementCommit est définie sur true, le client supprime immédiatement la ou les licences locales, sans attendre la confirmation du serveur de licences qu’il a reçu la demande de retour des licences. Le serveur de licences Adobe Access doit traiter la demande et envoyer une réponse au client. Il appartient au serveur de licences de décider si le serveur de licences répond réellement à la demande (par exemple, décréter un nombre de licences pour l’utilisateur donné).

* La classe du gestionnaire de requêtes est com.adobe.flashaccess.sdk.protocol.prenereturn.LicenseReturnHandler.
* La classe du message de demande est com.adobe.flashaccess.sdk.protocol.prenereturn.LicenseReturnRequestMessage

La version minimale du SDK Adobe Access requise est la version 5 ; l’URL de requête sera &quot; `/flashaccess/lreturn/v5`&quot;. Comme pour le désenregistrement de domaine, le serveur doit utiliser `getRequestPhase()` pour déterminer si le client prévisualise un retour de licence.
