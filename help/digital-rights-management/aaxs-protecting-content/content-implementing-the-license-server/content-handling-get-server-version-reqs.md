---
seo-title: Gestion des demandes Get Server Version
title: Gestion des demandes Get Server Version
uuid: a3084faa-cf3d-45cc-a244-298308c4cf15
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gestion des demandes Get Server Version{#handling-get-server-version-requests}

Adobe Access client 3.0 et versions ultérieures envoient une demande Get Server Version afin de déterminer les fonctionnalités du serveur. Tous les serveurs utilisant Adobe Access SDK 3.0 et versions ultérieures doivent mettre en oeuvre la prise en charge des demandes Get Server Version.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* L’URL de demande doit être &quot;URL du serveur de licence dans les métadonnées&quot; + &quot;/flashaccess/getServerVersion/v3&quot;

Pour Adobe Access SDK 4.0 et versions ultérieures, la réponse à une demande Get Server Version indique aux clients que le serveur prend en charge les versions 3 et 4 du protocole Adobe Access.
