---
seo-title: Détection de restauration
title: Détection de restauration
uuid: fc80c98f-7ee5-414b-87fe-0dbb8d4f6019
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# Détection de restauration {#rollback-detection}

Si votre implémentation d’Adobe Access utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de la fenêtre de lecture), Adobe recommande vivement que le serveur garde le suivi du compteur d’annulation et utilise AIR ou SWF pour autoriser la mise en vente.

Le compteur d&#39;annulation est envoyé au serveur dans la plupart des requêtes du client. Si votre implémentation d&#39;Adobe Access ne nécessite pas le compteur d&#39;annulation, elle peut être ignorée. Dans le cas contraire, Adobe recommande que le serveur stocke l’ID d’ordinateur aléatoire (obtenu à l’aide `MachineToken.getMachineId().getUniqueId()`) et la valeur actuelle du compteur dans une base de données. Pour plus d’informations sur l’incrémentation et le suivi du compteur d’annulation, voir ClientState dans Référence *de l’API d’accès* Adobe et détection *de* restauration dans *Utilisation du SDK d’accès Adobe pour la protection du contenu*.
