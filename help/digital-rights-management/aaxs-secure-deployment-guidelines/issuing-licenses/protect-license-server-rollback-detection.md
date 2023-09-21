---
title: Détection de restauration
description: Détection de restauration
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Détection de restauration {#rollback-detection}

Si votre mise en oeuvre de Adobe Access utilise des règles de fonctionnement qui exigent que le client conserve l’état (par exemple, l’intervalle de fenêtre de lecture), Adobe recommande vivement que le serveur suive le compteur de restauration et utilise les listes autorisées AIR ou SWF.

Le compteur de restauration est envoyé au serveur dans la plupart des requêtes du client. Si votre mise en oeuvre de Adobe Access ne nécessite pas de compteur de restauration, elle peut être ignorée. Sinon, Adobe recommande que le serveur stocke l’ID de machine aléatoire, obtenu à l’aide de `MachineToken.getMachineId().getUniqueId()`: et la valeur actuelle du compteur dans une base de données. Pour plus d’informations sur l’incrémentation et le suivi du compteur de restauration, voir ClientState dans *Référence de l’API Adobe Access* et *Détection de restauration* in *Utilisation du SDK Adobe Access pour la protection du contenu*.
