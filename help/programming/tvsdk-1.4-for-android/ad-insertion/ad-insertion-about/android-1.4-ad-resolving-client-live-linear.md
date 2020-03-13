---
description: Pour le contenu en direct/linéaire, TVSDK remplace une partie du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-description: Pour le contenu en direct/linéaire, TVSDK remplace une partie du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-title: Résolution et insertion d’annonces dynamiques/linéaires
title: Résolution et insertion d’annonces dynamiques/linéaires
uuid: a63c97c3-00c5-4dee-a42c-30b70e432b93
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Résolution et insertion d’annonces dynamiques/linéaires {#live-linear-ad-resolving-and-insertion}

Pour le contenu en direct/linéaire, TVSDK remplace une partie du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.

Avant et pendant la lecture, TVSDK résout les publicités connues, remplace certaines parties du contenu principal par des coupures publicitaires de la même durée et recalcule le scénario virtuel, le cas échéant. Les positions des coupures publicitaires sont spécifiées par des points de repère définis par le manifeste.

TVSDK insère des publicités de différentes manières :

* **Pré-rouler**, au début du contenu.
* **Mid-roll**, au milieu du contenu.

TVSDK accepte la coupure publicitaire même si la durée est plus longue ou plus courte que la durée de remplacement du point de repère. Par défaut, TVSDK prend en charge le `#EXT-X-CUE` signal en tant que marqueur publicitaire valide lors de la résolution et du placement des publicités. Ce marqueur requiert le champ de métadonnées `DURATION` en secondes et l’identifiant unique du signal. Par exemple :

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Vous pouvez définir et vous abonner à d’autres indices (balises).

Après  de lecture, le moteur vidéo actualise régulièrement le fichier manifeste. TVSDK résout toute nouvelle publicité et insère les publicités lorsqu’un point de repère est rencontré dans le flux en direct ou linéaire défini dans le manifeste. Une fois les publicités résolues et insérées, TVSDK calcule à nouveau la chronologie virtuelle et distribue un `TimelineItemsUpdatedEventListener.onTimelineUpdated` .
