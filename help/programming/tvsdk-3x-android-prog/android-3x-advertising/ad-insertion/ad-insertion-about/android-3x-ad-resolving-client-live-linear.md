---
description: Pour le contenu en direct/linéaire, TVSDK remplace une partie du contenu de la diffusion principale par une coupure publicitaire de la même durée, de sorte que la durée de la chronologie reste la même.
title: Résoudre et insérer une publicité Live/linéaire
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Résoudre et insérer des publicités actives/linéaires {#resolve-and-insert-live-linear-ad}

Pour le contenu en direct/linéaire, TVSDK remplace une partie du contenu de la diffusion principale par une coupure publicitaire de la même durée, de sorte que la durée de la chronologie reste la même.

Avant et pendant la lecture, TVSDK résout les publicités connues, remplace certaines parties du contenu principal par des coupures publicitaires de la même durée et recalcule la chronologie virtuelle, si nécessaire. Les positions des coupures publicitaires sont spécifiées par des points de repère définis par le manifeste.

TVSDK insère des publicités de la manière suivante :

* **Pré-roll**, qui est placé avant le contenu.
* **Mid-roll**, qui est placé au milieu du contenu.

TVSDK accepte la coupure publicitaire même si la durée est plus longue ou plus courte que la durée de remplacement du point de repère. Par défaut, TVSDK prend en charge la variable `#EXT-X-CUE` Indicateur comme marqueur de publicité valide lors de la résolution et du placement de publicités. Ce marqueur nécessite le champ de métadonnées `DURATION` valeur à exprimer en secondes et identifiant unique du repère. Par exemple :

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Vous pouvez définir et abonner des repères (balises) supplémentaires.

Une fois la lecture lancée, le moteur vidéo actualise régulièrement le fichier manifeste. TVSDK résout les nouvelles publicités et insère les publicités lorsqu’un point de repère est rencontré dans le flux en direct ou linéaire qui a été défini dans le manifeste. Une fois les publicités résolues et insérées, TVSDK calcule à nouveau la chronologie virtuelle et distribue une `TimelineItemsUpdatedEventListener.onTimelineUpdated` .
