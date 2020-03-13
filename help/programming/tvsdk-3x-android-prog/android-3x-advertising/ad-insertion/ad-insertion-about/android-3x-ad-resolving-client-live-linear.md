---
description: Pour le contenu en direct/linéaire, TVSDK remplace une partie du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-description: Pour le contenu en direct/linéaire, TVSDK remplace une partie du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-title: Résolution et insertion d’une publicité dynamique/linéaire
title: Résolution et insertion d’une publicité dynamique/linéaire
uuid: 722569f2-d260-4fcc-b6b9-01d86aa00e28
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Résolution et insertion de publicités dynamiques/linéaires {#resolve-and-insert-live-linear-ad}

Pour le contenu en direct/linéaire, TVSDK remplace une partie du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.

Avant et pendant la lecture, TVSDK résout les publicités connues, remplace certaines parties du contenu principal par des coupures publicitaires de la même durée et recalcule le scénario virtuel, le cas échéant. Les positions des coupures publicitaires sont spécifiées par des points de repère définis par le manifeste.

TVSDK insère des publicités de différentes manières :

* **Pré-roll**, placé avant le contenu.
* **Menu déroulant** central, placé au milieu du contenu.

TVSDK accepte la coupure publicitaire même si la durée est plus longue ou plus courte que la durée de remplacement du point de repère. Par défaut, TVSDK prend en charge le `#EXT-X-CUE` signal en tant que marqueur publicitaire valide lors de la résolution et du placement des publicités. Ce marqueur requiert que la `DURATION` valeur du champ de métadonnées soit exprimée en secondes et que l’identifiant unique du signal soit spécifié. Par exemple :

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Vous pouvez définir et vous abonner à d’autres indices (balises).

Après  de lecture, le moteur vidéo actualise régulièrement le fichier manifeste. TVSDK résout toute nouvelle publicité et insère les publicités lorsqu’un point de repère est rencontré dans le flux en direct ou linéaire défini dans le manifeste. Une fois les publicités résolues et insérées, TVSDK calcule à nouveau la chronologie virtuelle et distribue un `TimelineItemsUpdatedEventListener.onTimelineUpdated` .