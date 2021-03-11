---
title: Gestion des demandes Get Server Version
description: Gestion des demandes Get Server Version
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Gestion des demandes Get Server Version {#handling-get-server-version-requests}

Adobe Access client 3.0 et version ultérieure envoie une demande Get Server Version afin de déterminer les fonctionnalités du serveur. Tous les serveurs utilisant Adobe Access SDK 3.0 et versions ultérieures doivent mettre en oeuvre la prise en charge des demandes Get Server Version.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* L’URL de demande doit être &quot;URL du serveur de licence dans les métadonnées&quot; + &quot;/flashaccess/getServerVersion/v3&quot;

Pour le SDK d’accès aux Adobes version 4.0 et ultérieure, la réponse à une demande Get Server Version indique aux clients que le serveur prend en charge les versions 3 et 4 du protocole Adobe Access.
