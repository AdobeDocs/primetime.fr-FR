---
description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des pauses publicitaires en épinglant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.
seo-description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des pauses publicitaires en épinglant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.
seo-title: Résolution et insertion de la publicité VOD
title: Résolution et insertion de la publicité VOD
uuid: 69853c16-e252-472e-b33a-7a0e0c4b95dd
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Résolution et insertion de publicités VOD {#resolve-and-insert-vod-ad}

Pour le contenu vidéo à la demande (VOD), TVSDK insère des pauses publicitaires en épinglant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.

Avant la lecture, TVSDK résout les publicités connues, insère les coupures publicitaires dans le contenu principal, comme décrit par une chronologie renvoyée par la prise de décision publicitaire Adobe Primetime, et recalcule le cas échéant la chronologie virtuelle.

TVSDK insère des publicités de différentes manières :

* **Pré-roll**, placé avant le contenu.
* **Menu déroulant** intermédiaire, qui se trouve au milieu du contenu.
* **Post-roll**, placé après le contenu.

>[!TIP]
>
>Une fois le de lecture , aucune modification supplémentaire ne peut se produire dans le contenu.

Les publicités ne peuvent pas être :

* Inséré
* Supprimé

   Par exemple, vous ne pouvez pas supprimer des publicités intégrées du contenu pour  une expérience  sans publicité.
* Remplacé

   Par exemple, vous ne pouvez pas remplacer les publicités intégrées par des publicités ciblées.

