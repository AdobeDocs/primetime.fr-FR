---
title: Gestion des demandes de retour de licence
description: Gestion des demandes de retour de licence
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Gestion des demandes de retour de licence{#handle-license-return-requests}

Si l’application cliente doit renvoyer une licence, elle appelle la méthode `DRMManager.returnVoucher()` API Actionscript pour lancer le processus. Cette API peut fonctionner dans une `immediateCommit` ou un `confirmFirst` mode . If `immediateCommit` est défini sur `true`, le client supprime alors la ou les licences locales immédiatement sans attendre la confirmation du serveur de licences qu’il a reçu la demande de renvoi de la ou des licences. Le serveur de licences Adobe Primetime DRM doit traiter la demande et envoyer une réponse au client. Le serveur de licences décide si le serveur traite ou non la demande, par exemple décréter un nombre de licences pour un utilisateur spécifié.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* La classe de message de requête est `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

Le minimum `Adobe Primetime DRM` La version du SDK requise est la version 5 ; l’URL de la requête est &quot; [!DNL /flashaccess/lreturn/v5]&quot;. Comme pour le désenregistrement de domaine, le serveur utilise `getRequestPhase()` pour déterminer si le client peut prévisualiser un retour de licence.
