---
title: Gestion des demandes Get Server Version
description: Gestion des demandes Get Server Version
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Gestion des demandes Get Server Version{#handling-get-server-version-requests}

Adobe Access Client 3.0 et versions ultérieures envoient une demande Get Server Version afin de déterminer les fonctionnalités du serveur. Tous les serveurs utilisant Adobe Access SDK 3.0 et versions ultérieures doivent mettre en oeuvre la prise en charge des demandes Get Server Version.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* La classe de message de requête est `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* L’URL de demande doit être &quot;URL du serveur de licences dans les métadonnées&quot; + &quot;/flashaccess/getServerVersion/v3&quot;

Pour Adobe Access SDK 4.0 et versions ultérieures, la réponse à une demande Get Server Version indique aux clients que le serveur prend en charge les versions 3 et 4 du protocole Adobe Access.
