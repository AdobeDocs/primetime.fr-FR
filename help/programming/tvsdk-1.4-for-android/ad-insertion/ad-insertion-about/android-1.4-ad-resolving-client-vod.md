---
description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des pauses publicitaires en épinglant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.
seo-description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des pauses publicitaires en épinglant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.
seo-title: Résolution et insertion de publicités VOD
title: Résolution et insertion de publicités VOD
uuid: 33280792-ad08-41c1-b180-cc2159e8137c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Résolution et insertion de publicités VOD{#vod-ad-resolving-and-insertion}

Pour le contenu vidéo à la demande (VOD), TVSDK insère des pauses publicitaires en épinglant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.

Avant la lecture, TVSDK résout les publicités connues, insère les coupures publicitaires dans le contenu principal, comme décrit par une chronologie renvoyée par la prise de décision publicitaire Adobe Primetime, et recalcule le cas échéant la chronologie virtuelle.

TVSDK insère des publicités de différentes manières :

* **Pré-roll**, qui se trouve avant le contenu.
* **Mid-roll**, qui se trouve dans le contenu.
* **Post-roll**, qui suit le contenu.

Une fois le de lecture , aucune modification supplémentaire ne peut se produire dans le contenu. Les publicités ne peuvent pas être :

* Inséré
* Supprimé

   Par exemple, vous ne pouvez pas supprimer des publicités intégrées du contenu pour  une expérience  sans publicité.
* Remplacé

   Par exemple, vous ne pouvez pas remplacer les publicités intégrées par des publicités ciblées.

