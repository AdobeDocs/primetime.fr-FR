---
seo-title: Gestion des demandes Get Server Version
title: Gestion des demandes Get Server Version
uuid: 6e287f58-2ad2-428a-a76a-6847d06b0fd8
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Gestion des demandes Get Server Version {#handle-get-server-version-requests}

Le client DRM Adobe Primetime 3.0 ou version ultérieure envoie une demande Get Server Version afin de déterminer les fonctionnalités du serveur. Tous les serveurs utilisant Primetime DRM SDK 3.0 ou version ultérieure doivent implémenter la prise en charge des demandes Get Server Version.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* L’URL de demande doit être &quot;URL du serveur de licences dans les métadonnées&quot; + &quot; [!DNL /flashaccess/getServerVersion/v3]&quot;

Pour le SDK DRM 4.0 de Primetime ou version ultérieure, la réponse à une demande Get Server Version indique aux clients que le serveur prend en charge les versions 3 et 4 du protocole DRM de Primetime.
