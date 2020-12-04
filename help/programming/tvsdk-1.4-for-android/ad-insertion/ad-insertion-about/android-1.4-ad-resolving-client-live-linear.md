---
description: Pour le contenu en direct/linéaire, TVSDK remplace un morceau du contenu du flux principal par une coupure publicitaire de même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-description: Pour le contenu en direct/linéaire, TVSDK remplace un morceau du contenu du flux principal par une coupure publicitaire de même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-title: Résolution et insertion d’annonces dynamiques/linéaires
title: Résolution et insertion d’annonces dynamiques/linéaires
uuid: a63c97c3-00c5-4dee-a42c-30b70e432b93
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Résolution et insertion des publicités en direct/linéaire {#live-linear-ad-resolving-and-insertion}

Pour le contenu en direct/linéaire, TVSDK remplace un morceau du contenu du flux principal par une coupure publicitaire de même durée, de sorte que la durée du plan de montage chronologique reste la même.

Avant et pendant la lecture, TVSDK résout les publicités connues, remplace certaines parties du contenu principal par des coupures publicitaires de la même durée et recalcule la chronologie virtuelle, si nécessaire. Les positions des coupures publicitaires sont spécifiées par des indices définis par le manifeste.

TVSDK insère des publicités de différentes manières :

* **Pré-roll**, au début du contenu.
* **Menu déroulant**, au milieu du contenu.

TVSDK accepte la coupure publicitaire même si la durée est supérieure ou inférieure à la durée de remplacement du point de repère. Par défaut, TVSDK prend en charge l’indice `#EXT-X-CUE` en tant que marqueur publicitaire valide lors de la résolution et du placement des publicités. Ce marqueur requiert le champ de métadonnées `DURATION` en secondes et l’identifiant unique du signal. Par exemple :

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Vous pouvez définir et vous abonner à d’autres indices (balises).

Après les débuts de lecture, le moteur vidéo actualise régulièrement le fichier manifeste. TVSDK résout toute nouvelle publicité et insère les publicités lorsqu’un point de repère est détecté dans le flux en direct ou linéaire défini dans le manifeste. Une fois les publicités résolues et insérées, TVSDK calcule à nouveau la chronologie virtuelle et distribue un événement `TimelineItemsUpdatedEventListener.onTimelineUpdated`.
