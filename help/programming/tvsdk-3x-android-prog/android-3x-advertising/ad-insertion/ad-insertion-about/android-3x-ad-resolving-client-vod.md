---
description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.
seo-description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.
seo-title: Résoudre et insérer une publicité VOD
title: Résoudre et insérer une publicité VOD
uuid: b7124cab-441b-4b38-ac83-300ab9e5f9ec
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Résolution et insertion de publicités VOD {#resolve-and-insert-vod-ad}

Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en épinglant les publicités dans le contenu principal afin que la durée de la chronologie augmente.

Avant la lecture, TVSDK résout les publicités connues, insère les coupures publicitaires dans le contenu principal, comme décrit dans une chronologie renvoyée par la prise de décision publicitaire Adobe Primetime, et recalcule la chronologie virtuelle, si nécessaire.

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