---
title: Gestion des demandes Get Server Version
description: Gestion des demandes Get Server Version
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Gérer les demandes d&#39;obtention de version de serveur {#handle-get-server-version-requests}

Adobe Primetime DRM client 3.0 ou version ultérieure envoie une demande Get Server Version pour déterminer les fonctionnalités du serveur. Tous les serveurs utilisant Primetime DRM SDK 3.0 ou version ultérieure doivent implémenter la prise en charge des demandes Get Server Version.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* La classe de message de demande est `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* L’URL de demande doit être &quot;URL du serveur de licences dans les métadonnées&quot; + &quot; [!DNL /flashaccess/getServerVersion/v3]&quot;

Pour le SDK DRM 4.0 de Primetime ou version ultérieure, la réponse à une demande Get Server Version indique aux clients que le serveur prend en charge les versions 3 et 4 du protocole DRM de Primetime.
