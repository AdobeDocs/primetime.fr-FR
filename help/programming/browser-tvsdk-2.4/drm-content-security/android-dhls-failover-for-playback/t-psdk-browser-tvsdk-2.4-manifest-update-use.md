---
description: Vous pouvez activer cette fonction et vérifier si des événements connexes sont associés.
title: Utiliser la mise à jour de manifeste principal en direct
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---


# Utilisation de la mise à jour de manifeste maître en direct{#use-live-master-manifest-update}

Vous pouvez activer cette fonction et vérifier si des événements connexes sont associés.

1. Pour activer les mises à jour de manifeste principal en direct, définissez la fréquence de mise à jour (en minutes) en définissant la propriété `NetworkConfiguration.masterUpdateInterval`.
1. Si vous le souhaitez, effectuez le suivi des mises à jour de manifeste réussies en écoutant le événement `MediaPlayerItemEvent.MASTER_UPDATED`.
