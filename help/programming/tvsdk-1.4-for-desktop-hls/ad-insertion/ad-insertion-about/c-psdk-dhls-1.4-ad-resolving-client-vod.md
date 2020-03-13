---
description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des pauses publicitaires en épinglant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.
seo-description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des pauses publicitaires en épinglant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.
seo-title: Résolution et insertion de publicités VOD
title: Résolution et insertion de publicités VOD
uuid: c1017483-5b4f-4d71-9589-fb2327b4572b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Résolution et insertion de publicités VOD{#vod-ad-resolving-and-insertion}

Pour le contenu vidéo à la demande (VOD), TVSDK insère des pauses publicitaires en épinglant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.

Avant la lecture, TVSDK résout les publicités connues, insère les coupures publicitaires dans le contenu principal, comme décrit par une chronologie renvoyée par TVSDK, et recalcule le cas échéant la chronologie virtuelle.

TVSDK insère des publicités de différentes manières :

* **Pré-roll**, qui se trouve avant le contenu.
* **Mid-roll**, qui se trouve dans le contenu.
* **Post-roll**, qui suit le contenu.

>[!IMPORTANT]
>
>Lors de l’implémentation d’une personnalisation `AdPolicySelector`, une stratégie différente peut être donnée à chaque type de `AdBreakTimelineItem` (preroll, mid-roll ou post-roll) dans `AdPolicyInfo`, en fonction du type de la `AdBreakTimelineItem`. Par exemple, vous pouvez conserver le contenu mid-roll après sa lecture, mais supprimer le contenu pre-roll après sa lecture.

Une fois le de lecture , aucune modification supplémentaire ne peut se produire dans le contenu. Les publicités ne peuvent pas être :

* Inséré
* Supprimé

   Par exemple, vous ne pouvez pas supprimer des publicités intégrées du contenu pour  une expérience  sans publicité.
* Remplacé

   Par exemple, vous ne pouvez pas remplacer les publicités intégrées par des publicités ciblées.

