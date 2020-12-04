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

Si votre mise en oeuvre d&#39;Adobe Access utilise des règles de fonctionnement qui exigent que le client conserve l&#39;état (par exemple, l&#39;intervalle de lecture), l&#39;Adobe recommande vivement que le serveur garde le suivi du compteur d&#39;annulation et utilise AIR ou SWF pour autoriser la mise en vente.

Le compteur d&#39;annulation est envoyé au serveur dans la plupart des requêtes du client. Si votre mise en oeuvre d&#39;Adobe Access ne nécessite pas le compteur d&#39;annulation, elle peut être ignorée. Dans le cas contraire, l’Adobe recommande au serveur de stocker l’ID d’ordinateur aléatoire (obtenu à l’aide de `MachineToken.getMachineId().getUniqueId()`) et la valeur de compteur actuelle dans une base de données. Pour plus d&#39;informations sur l&#39;incrémentation et le suivi du compteur d&#39;annulation, consultez ClientState dans *Adobe Access API Reference* et *Rollback detection* dans *Utilisation du SDK Adobe Access pour la protection du contenu*.
