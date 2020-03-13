---
seo-title: Détection de restauration
title: Détection de restauration
uuid: fc80c98f-7ee5-414b-87fe-0dbb8d4f6019
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Détection de restauration{#rollback-detection}

Si votre implémentation d’Adobe Access utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de la fenêtre de lecture), Adobe recommande vivement au serveur de suivre le compteur d’annulation et d’utiliser la liste blanche AIR ou SWF.

Le compteur de restauration est envoyé au serveur dans la plupart des requêtes du client. Si votre implémentation d’Adobe Access ne nécessite pas le compteur d’annulation, elle peut être ignorée. Dans le cas contraire, Adobe conseille au serveur de stocker l’ID d’ordinateur aléatoire (obtenu à l’aide `MachineToken.getMachineId().getUniqueId()`) et la valeur de compteur actuelle dans une base de données. Pour plus d’informations sur l’incrémentation et le suivi du compteur d’annulation, voir ClientState dans *Adobe Access API Reference* and *Rollback detection* in *Using the Adobe Access SDK for Protecting Content*.
