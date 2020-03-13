---
description: Vous pouvez activer cette fonctionnalité et rechercher les  de connexes.
seo-description: Vous pouvez activer cette fonctionnalité et rechercher les  de connexes.
seo-title: Utilisation de la mise à jour de manifeste maître en direct
title: Utilisation de la mise à jour de manifeste maître en direct
uuid: 4ec665ab-b7ce-4a45-a251-13a07eb4d789
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Utilisation de la mise à jour de manifeste maître en direct{#use-live-master-manifest-update}

Vous pouvez activer cette fonctionnalité et rechercher les  de connexes.

1. Pour activer les mises à jour de manifeste principal en direct, définissez la fréquence de mise à jour (en minutes) en définissant la `NetworkConfiguration.masterUpdateInterval` propriété.
1. Si vous le souhaitez, effectuez le suivi des mises à jour de manifeste réussies en écoutant le  du `MediaPlayerItemEvent.MASTER_UPDATED` .
