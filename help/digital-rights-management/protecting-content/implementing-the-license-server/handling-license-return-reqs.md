---
seo-title: Gérer les demandes de retour de licence
title: Gérer les demandes de retour de licence
uuid: 994df5af-476a-4ee8-b371-8900241be83d
translation-type: tm+mt
source-git-commit: ''

---


# Gérer les demandes de retour de licence{#handle-license-return-requests}

Si l’application cliente doit renvoyer une licence, elle appelle l’API `DRMManager.returnVoucher()` Actionscript pour lancer le processus. Cette API peut fonctionner en mode `immediateCommit` ou en `confirmFirst` mode. Si `immediateCommit` est défini sur `true`, le client supprime immédiatement la ou les licences locales sans attendre la confirmation du serveur de licences qu’il a reçu la demande de renvoi des licences. Le serveur de licences DRM d’Adobe Primetime doit traiter la demande et envoyer une réponse au client. Le serveur de licences décide si le serveur de licences traite ou non la demande, par exemple décréter un nombre de licences pour un utilisateur spécifié.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

La version minimale `Adobe Primetime DRM` du SDK requise est la version 5 ; l’URL de demande est &quot; [!DNL /flashaccess/lreturn/v5]&quot;. Comme pour le désenregistrement de domaine, le serveur utilise `getRequestPhase()` pour déterminer si le client peut prévisualisation un retour de licence.
