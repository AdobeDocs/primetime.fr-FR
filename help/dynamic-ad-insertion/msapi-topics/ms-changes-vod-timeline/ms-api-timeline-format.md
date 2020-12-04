---
description: Vous pouvez spécifier ou remplacer des chronologies pour les coupures publicitaires dans le contenu VOD à l’aide d’une liste formatée de segments de publicité et de contenu appelée capsules.
seo-description: Vous pouvez spécifier ou remplacer des chronologies pour les coupures publicitaires dans le contenu VOD à l’aide d’une liste formatée de segments de publicité et de contenu appelée capsules.
seo-title: Format de chronologie VOD
title: Format de chronologie VOD
uuid: 6daaf605-e5ee-48dc-a222-a5973b3d915a
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Format de chronologie VOD {#vod-timeline-format}

Vous pouvez spécifier ou remplacer des chronologies pour les coupures publicitaires dans le contenu VOD à l’aide d’une liste formatée de segments de publicité et de contenu appelée capsules.

## Pods {#section_606E9456E25E41C8B8537A023DDD96CE}

Une capsule est une coupure publicitaire ou un segment de contenu. Une chronologie se compose d’une séquence de capsules, séparées par des points-virgules. Les types de capsules suivants existent :

### Saut de publicité

```
B,duration,maximum_number_of_ads,position
```

La durée est en secondes, avec une précision de 0,001 (millisecondes); nombre de publicités est un entier. La position est l’une des suivantes :
* **n** Aucun — aucune publicité
* **p** Avant le lancement — avant le contenu
* **m** Mid-roll — dans le contenu
* **t** Post-roll — après le contenu

Par exemple, `B,60,2,p` représente une coupure d’une minute pour un maximum de 2 publicités avant le contenu.

### Segment de contenu - chapitre

```
C,duration,number_of_lots
```

La durée est en secondes, avec une précision de 0,001 (millisecondes); nombre de lots (sections de contenu) est un entier. Par exemple, `C,300,1` représente une seule section de contenu de cinq minutes.