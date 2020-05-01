---
description: Pour le contenu en direct/linéaire, le navigateur TVSDK remplace un morceau du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-description: Pour le contenu en direct/linéaire, le navigateur TVSDK remplace un morceau du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-title: Résolution et insertion d’annonces dynamiques/linéaires
title: Résolution et insertion d’annonces dynamiques/linéaires
uuid: 18c6733a-e827-4b1c-9cd5-796d57cbdb05
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Résolution et insertion d’annonces dynamiques/linéaires{#live-linear-ad-resolving-and-insertion}

Pour le contenu en direct/linéaire, le navigateur TVSDK remplace un morceau du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.

Avant et pendant la lecture, le navigateur TVSDK résout les publicités connues, remplace certaines parties du contenu principal par des coupures publicitaires de la même durée et recalcule la chronologie virtuelle, si nécessaire. Les positions des coupures publicitaires sont spécifiées par des indices définis par le manifeste.

Le navigateur TVSDK insère les publicités de différentes manières :

* **Pré-roll**, qui se trouve au début du contenu.

Le navigateur TVSDK accepte la coupure publicitaire même si la durée est supérieure ou inférieure à la durée de remplacement du point de repère. Par défaut, le navigateur TVSDK prend en charge l’ `#EXT-X-CUE` indice en tant que marqueur publicitaire valide lors de la résolution et du placement des publicités. Ce marqueur requiert le champ de métadonnées `DURATION` en secondes et l’identifiant unique du repère. Par exemple :

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Vous pouvez définir et vous abonner à d’autres indices (balises).

Après les débuts de lecture, le moteur vidéo actualise régulièrement le fichier manifeste. Le navigateur TVSDK résout toute nouvelle publicité et insère les publicités lorsqu’un point de repère est détecté dans le flux en direct ou linéaire défini dans le manifeste. Une fois les publicités résolues et insérées, le navigateur TVSDK calcule à nouveau la chronologie virtuelle et distribue un `AdobePSDK.PSDKEventType.TIMELINE_UPDATED` événement.

>[!TIP]
>
>Pour les flux en direct, le navigateur TVSDK ne prend en charge que les publicités MP4 et HLS preroll et mid-roll.

