---
description: Pour le contenu en direct/linéaire, TVSDK remplace un morceau du contenu du flux principal par une coupure publicitaire de même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-description: Pour le contenu en direct/linéaire, TVSDK remplace un morceau du contenu du flux principal par une coupure publicitaire de même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-title: Résolution et insertion d’annonces dynamiques/linéaires
title: Résolution et insertion d’annonces dynamiques/linéaires
uuid: 69f287aa-b707-442b-8e07-16f81b242c4b
translation-type: tm+mt
source-git-commit: ''

---


# Résolution et insertion d’annonces dynamiques/linéaires{#live-linear-ad-resolving-and-insertion}

Pour le contenu en direct/linéaire, TVSDK remplace un morceau du contenu du flux principal par une coupure publicitaire de même durée, de sorte que la durée du plan de montage chronologique reste la même.

Avant et pendant la lecture, TVSDK résout les publicités connues, remplace certaines parties du contenu principal par des coupures publicitaires de la même durée et recalcule la chronologie virtuelle, si nécessaire. Les positions des coupures publicitaires sont spécifiées par des indices définis par le manifeste.

TVSDK insère des publicités de différentes manières :

* **Pré-roll**, qui se trouve au début du contenu.
* **Menu déroulant** intermédiaire, qui se trouve au milieu du contenu.

TVSDK accepte la coupure publicitaire même si la durée est supérieure ou inférieure à la durée de remplacement du point de repère. Par défaut, TVSDK prend en charge l’ `#EXT-X-CUE` indice en tant que marqueur publicitaire valide lors de la résolution et du placement des publicités. Ce marqueur requiert le champ de métadonnées `DURATION` en secondes et l’identifiant unique du repère. Par exemple :

```
#EXT-X-CUE:DURATION=27,ID="..."
```

>[!IMPORTANT]
>
>Lors de la mise en oeuvre d’une règle coutumière `AdPolicySelector`, une politique différente peut être appliquée aux programmes pré-roll, mid-roll et post-roll `AdBreakTimelineItem`dans `AdPolicyInfo`, qui est basée sur le type des `AdBreakTimelineItem`programmes. Par exemple, vous pouvez conserver le contenu de type milieu de lecture après sa lecture, mais supprimer le contenu avant lecture après sa lecture.

Après les débuts de lecture, le moteur vidéo actualise régulièrement le fichier manifeste. TVSDK résout toute nouvelle publicité et insère les publicités lorsqu’un point de repère est détecté dans le flux en direct ou linéaire défini dans le manifeste. Une fois les publicités résolues et insérées, TVSDK calcule à nouveau la chronologie virtuelle et distribue un `TimelineEvent.TIMELINE_UPDATED` événement.
