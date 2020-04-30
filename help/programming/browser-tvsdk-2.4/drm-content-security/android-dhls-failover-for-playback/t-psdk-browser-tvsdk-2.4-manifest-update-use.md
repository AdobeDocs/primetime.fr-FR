---
description: Vous pouvez activer cette fonction et vérifier si des événements connexes sont associés.
seo-description: Vous pouvez activer cette fonction et vérifier si des événements connexes sont associés.
seo-title: Utiliser la mise à jour de manifeste principal en direct
title: Utiliser la mise à jour de manifeste principal en direct
uuid: 4ec665ab-b7ce-4a45-a251-13a07eb4d789
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Utiliser la mise à jour de manifeste principal en direct{#use-live-master-manifest-update}

Vous pouvez activer cette fonction et vérifier si des événements connexes sont associés.

1. Pour activer les mises à jour du manifeste principal en direct, définissez la fréquence de mise à jour (en minutes) en définissant la `NetworkConfiguration.masterUpdateInterval` propriété.
1. Si vous le souhaitez, effectuez le suivi des mises à jour de manifeste réussies en écoutant le `MediaPlayerItemEvent.MASTER_UPDATED` événement.
