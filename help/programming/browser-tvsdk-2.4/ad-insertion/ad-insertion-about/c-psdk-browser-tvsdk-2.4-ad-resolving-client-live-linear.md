---
description: Pour le contenu en direct/linéaire, le kit de développement TVSDK du navigateur remplace une partie du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-description: Pour le contenu en direct/linéaire, le kit de développement TVSDK du navigateur remplace une partie du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.
seo-title: Résolution et insertion d’annonces dynamiques/linéaires
title: Résolution et insertion d’annonces dynamiques/linéaires
uuid: 18c6733a-e827-4b1c-9cd5-796d57cbdb05
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Résolution et insertion d’annonces dynamiques/linéaires{#live-linear-ad-resolving-and-insertion}

Pour le contenu en direct/linéaire, le kit de développement TVSDK du navigateur remplace une partie du contenu du flux principal par une coupure publicitaire de la même durée, de sorte que la durée du plan de montage chronologique reste la même.

Avant et pendant la lecture, le navigateur TVSDK résout les publicités connues, remplace certaines parties du contenu principal par des coupures publicitaires de la même durée et recalcule la chronologie virtuelle, le cas échéant. Les positions des coupures publicitaires sont spécifiées par des points de repère définis par le manifeste.

Le navigateur TVSDK insère les publicités de différentes manières :

* **Pré-roll**, qui se trouve au début du contenu.

Le navigateur TVSDK accepte la coupure publicitaire même si la durée est plus longue ou plus courte que la durée de remplacement du point de repère. Par défaut, le SDK du navigateur prend en charge le `#EXT-X-CUE` signal en tant que marqueur d’annonce valide lors de la résolution et du placement des publicités. Ce marqueur requiert le champ de métadonnées `DURATION` en secondes et l’identifiant unique du signal. Par exemple :

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Vous pouvez définir et vous abonner à d’autres indices (balises).

Après  de lecture, le moteur vidéo actualise régulièrement le fichier manifeste. Le navigateur TVSDK résout toute nouvelle publicité et insère les publicités lorsqu’un point de repère est rencontré dans le flux en direct ou linéaire défini dans le manifeste. Une fois les publicités résolues et insérées, le navigateur TVSDK calcule à nouveau le plan de montage chronologique virtuel et distribue un `AdobePSDK.PSDKEventType.TIMELINE_UPDATED` .

>[!TIP]
>
>Pour les flux en direct, le navigateur TVSDK prend uniquement en charge les publicités MP4 et HLS preroll et mid-roll.

