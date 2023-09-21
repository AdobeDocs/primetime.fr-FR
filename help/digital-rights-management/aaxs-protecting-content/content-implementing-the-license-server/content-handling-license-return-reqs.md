---
title: Gestion des demandes de retour de licence
description: Gestion des demandes de retour de licence
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Gestion des demandes de retour de licence{#handling-license-return-requests}

Si l’application cliente doit renvoyer une licence, elle appelle l’API Actionscript DRMManager.returnVoucher() pour lancer le processus. Cette API peut fonctionner en mode immediateCommit ou en mode confirmFirst . Si la valeur immediateCommit est définie sur true, le client supprime immédiatement la ou les licences locales, sans attendre la confirmation du serveur de licences qu’il a reçu la demande de renvoi de la ou des licences. Le serveur de licences Adobe Access doit traiter la demande et envoyer une réponse au client. C’est au serveur de licences de décider si le serveur de licences traite réellement la demande (par exemple, décréter un nombre de licences pour l’utilisateur donné).

* La classe du gestionnaire de requêtes est com.adobe.flashaccess.sdk.protocol.licencisereturn.LicenseReturnHandler
* La classe de message de demande est com.adobe.flashaccess.sdk.protocol.licencisereturn.LicenseReturnRequestMessage.

La version minimale du SDK Adobe Access requise est la version 5 ; l’URL de demande est &quot; `/flashaccess/lreturn/v5`&quot;. Comme pour le désenregistrement de domaine, le serveur doit utiliser `getRequestPhase()` pour déterminer si le client prévisualise un retour de licence.
