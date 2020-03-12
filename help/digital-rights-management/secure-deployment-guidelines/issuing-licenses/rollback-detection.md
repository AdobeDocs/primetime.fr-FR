---
description: Si votre implémentation d’Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de la fenêtre de lecture), Adobe recommande que le serveur effectue le suivi du compteur d’annulation et utilise la liste blanche AIR ou SWF.
seo-description: Si votre implémentation d’Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de la fenêtre de lecture), Adobe recommande que le serveur effectue le suivi du compteur d’annulation et utilise la liste blanche AIR ou SWF.
seo-title: Détection de restauration
title: Détection de restauration
uuid: f161ed41-488a-478a-b6a8-468cf6d11e89
translation-type: tm+mt
source-git-commit: 3fdef12b717bb6f70ca27d9278de61d709f8349c

---


# Détection de restauration {#rollback-detection}

Si votre implémentation d’Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de la fenêtre de lecture), Adobe recommande que le serveur effectue le suivi du compteur d’annulation et utilise la liste blanche AIR ou SWF.

Le compteur de restauration est envoyé au serveur dans la plupart des requêtes du client. Si votre implémentation de DRM Primetime ne nécessite pas le compteur de restauration, elle peut être ignorée. Dans le cas contraire, Adobe recommande au serveur de stocker l’ID d’ordinateur aléatoire, obtenu à l’aide de [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()), et la valeur actuelle du compteur dans une base de données.

Pour plus d’informations sur la manière d’incrémenter et de suivre le compteur d’annulation, voir [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) et détection de restauration.