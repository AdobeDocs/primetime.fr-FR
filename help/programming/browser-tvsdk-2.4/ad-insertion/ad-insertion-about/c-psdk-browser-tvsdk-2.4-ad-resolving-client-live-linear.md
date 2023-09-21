---
description: Pour le contenu en direct/linéaire, le TVSDK du navigateur remplace une partie du contenu de la diffusion principale par une coupure publicitaire de la même durée, de sorte que la durée de la chronologie reste la même.
title: Résoudre et insertion des publicités linéaires en direct
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Résoudre et insertion des publicités linéaires en direct{#live-linear-ad-resolving-and-insertion}

Pour le contenu en direct/linéaire, le TVSDK du navigateur remplace une partie du contenu de la diffusion principale par une coupure publicitaire de la même durée, de sorte que la durée de la chronologie reste la même.

Avant et pendant la lecture, le TVSDK du navigateur résout les publicités connues, remplace certaines parties du contenu principal par des coupures publicitaires de la même durée et recalcule la chronologie virtuelle, si nécessaire. Les positions des coupures publicitaires sont spécifiées par des points de repère définis par le manifeste.

Le navigateur TVSDK insère les publicités comme suit :

* **Pré-roll**, qui se trouve au début du contenu.

Le TVSDK du navigateur accepte la coupure publicitaire même si la durée est plus longue ou plus courte que la durée de remplacement du point de repère. Par défaut, le TVSDK du navigateur prend en charge la variable `#EXT-X-CUE` Indicateur comme marqueur de publicité valide lors de la résolution et du placement de publicités. Ce marqueur nécessite le champ de métadonnées `DURATION` en secondes et l’identifiant unique du repère. Par exemple :

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Vous pouvez définir et abonner des repères (balises) supplémentaires.

Une fois la lecture lancée, le moteur vidéo actualise régulièrement le fichier manifeste. Le TVSDK du navigateur résout toutes les nouvelles publicités et insère les publicités lorsqu’un point de repère est rencontré dans le flux en direct ou linéaire qui a été défini dans le manifeste. Une fois les publicités résolues et insérées, le TVSDK du navigateur calcule à nouveau la chronologie virtuelle et distribue une `AdobePSDK.PSDKEventType.TIMELINE_UPDATED` .

>[!TIP]
>
>Pour les flux en direct, le TVSDK du navigateur ne prend en charge que les publicités MP4 et HLS preroll et mid-roll.
