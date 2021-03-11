---
description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.
title: Résolution et insertion de publicités VOD
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Résolution et insertion de publicités VOD{#vod-ad-resolving-and-insertion}

Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.

Avant la lecture, TVSDK résout les publicités connues, insère les coupures publicitaires dans le contenu principal, comme décrit par une chronologie qui est renvoyée par TVSDK, et recalcule la chronologie virtuelle, si nécessaire.

TVSDK insère des publicités de différentes manières :

* **Pré-roll**, qui est avant le contenu.
* **Lecture intermédiaire**, qui se trouve dans le contenu.
* **Post-roll**, qui suit le contenu.

>[!IMPORTANT]
>
>Lors de l&#39;implémentation d&#39;une stratégie personnalisée `AdPolicySelector`, une stratégie différente peut être donnée à chaque type de `AdBreakTimelineItem` (pré-roll, mid-roll ou post-roll) dans `AdPolicyInfo`, en fonction du type de `AdBreakTimelineItem`. Par exemple, vous pouvez conserver le contenu de milieu de gamme après sa lecture, mais supprimer le contenu de pré-lecture après sa lecture.

Après les débuts de lecture, aucune modification supplémentaire ne peut être apportée au contenu. Les publicités ne peuvent pas être :

* Inséré
* Supprimé

   Par exemple, vous ne pouvez pas supprimer des publicités intégrées du contenu vers l’offre d’une expérience sans publicité.
* Remplacé

   Par exemple, vous ne pouvez pas remplacer les publicités intégrées par des publicités ciblées.

