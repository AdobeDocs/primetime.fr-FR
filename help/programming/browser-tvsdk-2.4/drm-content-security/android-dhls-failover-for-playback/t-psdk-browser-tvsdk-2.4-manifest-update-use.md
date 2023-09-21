---
description: Vous pouvez activer cette fonction et rechercher les événements associés.
title: Utilisation de la mise à jour du manifeste principal actif
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---

# Utilisation de la mise à jour du manifeste principal actif{#use-live-master-manifest-update}

Vous pouvez activer cette fonction et rechercher les événements associés.

1. Pour activer les mises à jour de manifeste principal en direct, définissez la fréquence de mise à jour (en minutes) en définissant la variable `NetworkConfiguration.masterUpdateInterval` .
1. Si vous le souhaitez, effectuez le suivi des mises à jour de manifeste réussies en écoutant les `MediaPlayerItemEvent.MASTER_UPDATED` .
