---
description: Si votre mise en oeuvre d’Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de temps de lecture), Adobe recommande que le serveur effectue le suivi du compteur de restauration et utilise les listes autorisées AIR ou SWF.
title: Détection de restauration
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Détection de restauration {#rollback-detection}

Si votre mise en oeuvre d’Adobe Primetime DRM utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de temps de lecture), Adobe recommande que le serveur effectue le suivi du compteur de restauration et utilise les listes autorisées AIR ou SWF.

Le compteur de restauration est envoyé au serveur dans la plupart des requêtes du client. Si votre mise en oeuvre de Primetime DRM ne nécessite pas de compteur de restauration, elle peut être ignorée. Sinon, Adobe recommande que le serveur stocke l’identifiant aléatoire de la machine, obtenu à l’aide de [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())et la valeur actuelle du compteur dans une base de données.

Pour plus d’informations sur l’incrémentation et le suivi du compteur de restauration, voir [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) et Détection de restauration.