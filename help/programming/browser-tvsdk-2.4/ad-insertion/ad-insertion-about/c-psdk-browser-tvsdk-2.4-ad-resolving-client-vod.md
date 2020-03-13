---
description: Pour le contenu vidéo à la demande (VOD), le navigateur TVSDK insère des pauses publicitaires en scindant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.
seo-description: Pour le contenu vidéo à la demande (VOD), le navigateur TVSDK insère des pauses publicitaires en scindant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.
seo-title: Résolution et insertion de publicités VOD
title: Résolution et insertion de publicités VOD
uuid: 34a30ae5-d553-4c5d-9829-8e5eaa41c104
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Résolution et insertion de publicités VOD{#vod-ad-resolving-and-insertion}

Pour le contenu vidéo à la demande (VOD), le navigateur TVSDK insère des pauses publicitaires en scindant les publicités dans le contenu principal afin que la durée du plan de montage chronologique augmente.

Avant la lecture, le navigateur TVSDK résout les publicités connues, insère les coupures publicitaires dans le contenu principal, comme décrit dans une chronologie renvoyée par Adobe Primetime et la prise de décision, et recalcule le cas échéant le scénario virtuel.

Le navigateur TVSDK insère les publicités de différentes manières :

* **Pré-roll**, qui se trouve avant le contenu.
* **Post-roll**, qui suit le contenu.

Une fois le de lecture , aucune modification supplémentaire ne peut se produire dans le contenu. Les publicités ne peuvent pas être :

* Inséré
* Supprimé

   Par exemple, vous ne pouvez pas supprimer des publicités intégrées du contenu pour  une expérience  sans publicité.
* Remplacé

   Par exemple, vous ne pouvez pas remplacer les publicités intégrées par des publicités ciblées.

