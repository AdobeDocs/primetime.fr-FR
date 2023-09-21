---
description: TVSDK insère dans la chronologie le contenu alternatif (publicités) correspondant au contenu principal.
title: Phase d’insertion publicitaire
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Phase d’insertion publicitaire{#ad-insertion-phase}

TVSDK insère dans la chronologie le contenu alternatif (publicités) correspondant au contenu principal.

Une fois la phase de résolution des publicités terminée, TVSDK dispose d’une liste classée de ressources publicitaires qui sont regroupées en coupures publicitaires. Chaque coupure publicitaire est positionnée sur la chronologie du contenu principal à l’aide d’une valeur de début exprimée en millisecondes (ms). Chaque publicité d’une coupure publicitaire possède une propriété duration également exprimée en ms. Les publicités d’une coupure publicitaire sont enchaînées les unes après les autres. Par conséquent, la durée d’une coupure publicitaire est égale à la somme des durées des publicités composées individuelles.

Le basculement peut se produire au cours de cette phase avec des conflits qui peuvent se produire sur la chronologie lors de l’insertion de publicités. Pour des combinaisons spécifiques de valeurs d’heure de début/durée de coupure publicitaire, les segments de publicité peuvent se chevaucher. Le chevauchement se produit lorsque la dernière partie d’une coupure publicitaire chevauche le début de la première publicité dans la coupure publicitaire suivante. Dans ce cas, TVSDK ignore la coupure publicitaire ultérieure et poursuit le processus d’insertion publicitaire avec l’élément suivant dans la liste jusqu’à ce que tous les coupures publicitaires soient insérés ou ignorés.

TVSDK émet une notification d’avertissement à propos de l’erreur et continue le traitement.
