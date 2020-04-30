---
description: Pour le contenu vidéo à la demande (VOD), le navigateur TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.
seo-description: Pour le contenu vidéo à la demande (VOD), le navigateur TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.
seo-title: Résolution et insertion de publicités VOD
title: Résolution et insertion de publicités VOD
uuid: 34a30ae5-d553-4c5d-9829-8e5eaa41c104
translation-type: tm+mt
source-git-commit: ''

---


# Résolution et insertion de publicités VOD{#vod-ad-resolving-and-insertion}

Pour le contenu vidéo à la demande (VOD), le navigateur TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.

Avant la lecture, le navigateur TVSDK résout les publicités connues, insère les coupures publicitaires dans le contenu principal, comme décrit par une chronologie qui est renvoyée à partir de la prise de décision publicitaire Adobe Primetime, et recalcule la chronologie virtuelle, si nécessaire.

Le navigateur TVSDK insère les publicités de différentes manières :

* **Pré-roll**, qui est avant le contenu.
* **Post-roll**, qui suit le contenu.

Après les débuts de lecture, aucune modification supplémentaire ne peut être apportée au contenu. Les publicités ne peuvent pas être :

* Inséré
* Supprimé

   Par exemple, vous ne pouvez pas supprimer des publicités intégrées du contenu vers l’offre d’une expérience sans publicité.
* Remplacé

   Par exemple, vous ne pouvez pas remplacer les publicités intégrées par des publicités ciblées.

