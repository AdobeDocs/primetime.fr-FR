---
description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.
title: Résoudre et insérer une publicité VOD
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Résolution et insertion de publicités VOD {#resolve-and-insert-vod-ad}

Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.

Avant la lecture, TVSDK résout les publicités connues, insère les coupures publicitaires dans le contenu principal, comme décrit par une chronologie qui est renvoyée à partir de la prise de décision de publicité Adobe Primetime, et recalcule la chronologie virtuelle, si nécessaire.

TVSDK insère des publicités de différentes manières :

* **Pré-roll**, qui est placé avant le contenu.
* **Menu déroulant** intermédiaire, qui se trouve au milieu du contenu.
* **Post-roll**, qui est placé après le contenu.

>[!TIP]
>
>Après les débuts de lecture, aucune modification supplémentaire ne peut être apportée au contenu.

Les publicités ne peuvent pas être :

* Inséré
* Supprimé

   Par exemple, vous ne pouvez pas supprimer des publicités intégrées du contenu vers l’offre d’une expérience sans publicité.
* Remplacé

   Par exemple, vous ne pouvez pas remplacer les publicités intégrées par des publicités ciblées.