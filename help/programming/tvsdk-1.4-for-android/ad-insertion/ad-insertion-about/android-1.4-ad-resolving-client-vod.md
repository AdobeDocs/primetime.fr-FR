---
description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.
seo-description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.
seo-title: Résolution et insertion de publicités VOD
title: Résolution et insertion de publicités VOD
uuid: 33280792-ad08-41c1-b180-cc2159e8137c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Résolution et insertion de publicités VOD{#vod-ad-resolving-and-insertion}

Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.

Avant la lecture, TVSDK résout les publicités connues, insère les coupures publicitaires dans le contenu principal, comme décrit par une chronologie qui est renvoyée à partir de la prise de décision de publicité Adobe Primetime, et recalcule la chronologie virtuelle, si nécessaire.

TVSDK insère des publicités de différentes manières :

* **Pré-roll**, qui est avant le contenu.
* **Lecture intermédiaire**, qui se trouve dans le contenu.
* **Post-roll**, qui suit le contenu.

Après les débuts de lecture, aucune modification supplémentaire ne peut être apportée au contenu. Les publicités ne peuvent pas être :

* Inséré
* Supprimé

   Par exemple, vous ne pouvez pas supprimer des publicités intégrées du contenu vers l’offre d’une expérience sans publicité.
* Remplacé

   Par exemple, vous ne pouvez pas remplacer les publicités intégrées par des publicités ciblées.

