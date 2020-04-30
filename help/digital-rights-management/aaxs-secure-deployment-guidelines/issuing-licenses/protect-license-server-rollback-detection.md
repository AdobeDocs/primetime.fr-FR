---
seo-title: Détection de restauration
title: Détection de restauration
uuid: fc80c98f-7ee5-414b-87fe-0dbb8d4f6019
translation-type: tm+mt
source-git-commit: ''

---


# Détection de restauration{#rollback-detection}

Si votre implémentation d’Adobe Access utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de la fenêtre de lecture), Adobe recommande vivement que le serveur conserve le suivi du compteur d’annulation et utilise la liste blanche AIR ou SWF.

Le compteur d&#39;annulation est envoyé au serveur dans la plupart des requêtes du client. Si votre implémentation d’Adobe Access ne nécessite pas le compteur d’annulation, il peut être ignoré. Dans le cas contraire, Adobe conseille au serveur de stocker l’ID d’ordinateur aléatoire (obtenu à l’aide `MachineToken.getMachineId().getUniqueId()`) et la valeur actuelle du compteur dans une base de données. Pour plus d’informations sur l’incrémentation et le suivi du compteur d’annulation, voir ClientState dans Référence *de l’API* Adobe Access et détection *de* restauration dans *Utilisation du SDK Adobe Access pour la protection du contenu*.
