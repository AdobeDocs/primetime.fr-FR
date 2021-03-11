---
description: Si votre implémentation de Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de lecture), l’Adobe recommande que le serveur garde le suivi du compteur d’annulation et utilise AIR ou SWF pour autoriser la mise en vente.
title: Détection de restauration
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Détection de restauration {#rollback-detection}

Si votre implémentation de Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de lecture), l’Adobe recommande que le serveur garde le suivi du compteur d’annulation et utilise AIR ou SWF pour autoriser la mise en vente.

Le compteur d&#39;annulation est envoyé au serveur dans la plupart des requêtes du client. Si votre mise en oeuvre de Primetime DRM ne nécessite pas le compteur d’annulation, elle peut être ignorée. Dans le cas contraire, l’Adobe recommande au serveur de stocker l’ID d’ordinateur aléatoire, obtenu à l’aide de [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) et de la valeur de compteur actuelle dans une base de données.

Pour plus d&#39;informations sur la façon d&#39;incrémenter et de suivre le compteur d&#39;annulation, voir [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) et Détection de restauration.