---
title: Fenêtre de lecture
description: Fenêtre de lecture
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---


# Fenêtre de lecture{#playback-window}

La fenêtre de lecture spécifie la durée de validité d’une licence après sa première utilisation pour lire du contenu protégé.

Exemple de cas d’utilisation : certains modèles d’entreprise autorisent une période de location de 30 jours, mais une fois la lecture commencée, celle-ci doit être terminée dans 48 heures. Dans ce cas, la durée de 48 heures de la licence correspond à la fenêtre de lecture.

**À partir de la version 5.3** - La fenêtre de lecture prend également en charge l’option d’activation ou de désactivation de l’arrêt en dur, qui indique si le contexte de déchiffrement de la lecture doit s’arrêter à l’expiration de la fenêtre de lecture (activée) ou continuer malgré l’expiration (désactivée).

>[!NOTE]
>
>L’option de blocage ne fonctionne pas correctement avec la fenêtre de lecture si elle est utilisée conjointement (la fenêtre de lecture ne sera pas respectée). La lecture du contenu avec la fenêtre de lecture sans arrêt sécurisé respecte la restriction de la fenêtre de lecture.

