---
description: Si votre implémentation d’Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de lecture), Adobe recommande que le serveur conserve le suivi du compteur d’annulation et utilise la liste blanche AIR ou SWF.
seo-description: Si votre implémentation d’Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de lecture), Adobe recommande que le serveur conserve le suivi du compteur d’annulation et utilise la liste blanche AIR ou SWF.
seo-title: Détection de restauration
title: Détection de restauration
uuid: f161ed41-488a-478a-b6a8-468cf6d11e89
translation-type: tm+mt
source-git-commit: 3fdef12b717bb6f70ca27d9278de61d709f8349c

---


# Détection de restauration {#rollback-detection}

Si votre implémentation d’Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de lecture), Adobe recommande que le serveur conserve le suivi du compteur d’annulation et utilise la liste blanche AIR ou SWF.

Le compteur d&#39;annulation est envoyé au serveur dans la plupart des requêtes du client. Si votre mise en oeuvre de Primetime DRM ne nécessite pas le compteur d’annulation, elle peut être ignorée. Dans le cas contraire, Adobe conseille au serveur de stocker l’ID d’ordinateur aléatoire, obtenu à l’aide de [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()), et la valeur de compteur actuelle dans une base de données.

Pour plus d&#39;informations sur la façon d&#39;incrémenter et de suivre le compteur d&#39;annulation, consultez [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) et Détection de restauration.