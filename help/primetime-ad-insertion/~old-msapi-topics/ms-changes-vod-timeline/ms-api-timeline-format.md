---
description: Vous pouvez spécifier ou remplacer des chronologies pour les coupures publicitaires dans le contenu VOD à l’aide d’une liste formatée de segments de publicité et de contenu appelés capsules.
title: Format de la chronologie VOD
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Format de la chronologie VOD {#vod-timeline-format}

Vous pouvez spécifier ou remplacer des chronologies pour les coupures publicitaires dans le contenu VOD à l’aide d’une liste formatée de segments de publicité et de contenu appelés capsules.

## Pods {#section_606E9456E25E41C8B8537A023DDD96CE}

Une capsule est une coupure publicitaire ou un segment de contenu. Une chronologie se compose d’une séquence de capsules, séparées par des points-virgules. Les types de capsules suivants existent :

### Coupure publicitaire

```
B,duration,maximum_number_of_ads,position
```

La durée est exprimée en secondes, avec une précision de 0,001 (millisecondes) ; le nombre de publicités est un entier. La position est l’une des suivantes : * **n** Aucun — aucune publicité * **p** preroll — avant le contenu * **m** Mid-roll — dans le contenu * **t** Post-roll — après le contenu

Par exemple : `B,60,2,p` représente une coupure d’une minute pour un maximum de 2 publicités avant le contenu.

### Segment de contenu - chapitre

```
C,duration,number_of_lots
```

La durée est exprimée en secondes, avec une précision de 0,001 (millisecondes) ; le nombre de lots (sections de contenu) est un entier. Par exemple : `C,300,1` représente une seule section de contenu de cinq minutes.