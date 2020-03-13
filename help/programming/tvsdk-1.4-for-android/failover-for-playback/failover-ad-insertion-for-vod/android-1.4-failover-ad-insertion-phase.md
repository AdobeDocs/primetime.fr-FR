---
description: TVSDK insère le contenu alternatif (publicités) dans la chronologie qui correspond au contenu principal.
seo-description: TVSDK insère le contenu alternatif (publicités) dans la chronologie qui correspond au contenu principal.
seo-title: Phase d'insertion publicitaire
title: Phase d'insertion publicitaire
uuid: 4a8e9578-6e95-44c0-b045-ae3c20da75e9
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Phase d&#39;insertion publicitaire{#ad-insertion-phase}

TVSDK insère le contenu alternatif (publicités) dans la chronologie qui correspond au contenu principal.

Une fois la phase de résolution des publicités terminée, TVSDK dispose d’un ordonné de ressources publicitaires regroupées en pauses publicitaires. Chaque coupure publicitaire est positionnée sur le plan de montage chronologique du contenu principal à l’aide d’une valeur -temps exprimée en millisecondes (ms). Chaque publicité d’une coupure publicitaire possède une propriété de durée qui est également exprimée en ms. Les publicités d’une coupure publicitaire sont liées les unes aux autres. Par conséquent, la durée d’une coupure publicitaire est égale à la somme des durées des publicités composées individuelles.

Le basculement peut survenir dans cette phase avec des conflits qui peuvent survenir sur le plan de montage chronologique lors de l’insertion d’une publicité. Pour des combinaisons spécifiques de valeurs de durée et d’heure de  des coupures publicitaires, les segments publicitaires peuvent se chevaucher. Le chevauchement se produit lorsque la dernière partie d’une coupure publicitaire chevauche le début de la première publicité au cours de la coupure publicitaire suivante. Dans ce cas, TVSDK ignore la coupure publicitaire ultérieure et poursuit le processus d’insertion publicitaire avec l’élément suivant sur le  jusqu’à ce que toutes les coupures publicitaires soient insérées ou ignorées.

TVSDK émet une notification d’avertissement concernant l’erreur et poursuit le traitement.
