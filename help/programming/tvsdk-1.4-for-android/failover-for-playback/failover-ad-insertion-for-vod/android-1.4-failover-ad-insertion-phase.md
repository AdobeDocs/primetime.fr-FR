---
description: TVSDK insère le contenu alternatif (publicités) dans la chronologie qui correspond au contenu principal.
title: Phase d'insertion publicitaire
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# Phase d’insertion publicitaire{#ad-insertion-phase}

TVSDK insère le contenu alternatif (publicités) dans la chronologie qui correspond au contenu principal.

Une fois la phase de résolution de la publicité terminée, TVSDK dispose d’une liste ordonnée de ressources publicitaires regroupées en pauses publicitaires. Chaque coupure publicitaire est positionnée sur la chronologie du contenu principal à l’aide d’une valeur de début-temps exprimée en millisecondes (ms). Chaque publicité d’une coupure publicitaire possède une propriété de durée qui est également exprimée en ms. Les publicités d’une coupure publicitaire sont chaînées les unes après les autres. Par conséquent, la durée d’une coupure publicitaire est égale à la somme des durées des publicités composées individuelles.

Le basculement peut survenir au cours de cette phase avec des conflits qui peuvent survenir sur le plan de montage chronologique lors de l&#39;insertion d&#39;une publicité. Pour des combinaisons spécifiques de valeurs de début/durée de coupure publicitaire, les segments publicitaires peuvent se chevaucher. Le chevauchement se produit lorsque la dernière partie d’une coupure publicitaire chevauche le début de la première publicité au cours de la coupure publicitaire suivante. Dans ce cas, TVSDK ignore la coupure publicitaire ultérieure et poursuit le processus d’insertion publicitaire avec l’élément suivant de la liste jusqu’à ce que toutes les coupures publicitaires soient insérées ou ignorées.

TVSDK émet une notification d’avertissement concernant l’erreur et poursuit le traitement.
