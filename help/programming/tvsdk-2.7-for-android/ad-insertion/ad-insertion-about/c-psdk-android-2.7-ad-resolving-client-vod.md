---
description: Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en répliquant les publicités dans le contenu principal afin que la durée de la chronologie augmente.
title: Résoudre et insérer une publicité VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Résoudre et insérer des publicités VOD {#resolve-and-insert-vod-ad}

Pour le contenu vidéo à la demande (VOD), TVSDK insère des coupures publicitaires en répliquant les publicités dans le contenu principal afin que la durée de la chronologie augmente.

Avant la lecture, TVSDK résout les publicités connues, insère les coupures publicitaires dans le contenu principal comme décrit par une chronologie qui est renvoyée à partir de la prise de décision publicitaire Adobe Primetime et recalcule la chronologie virtuelle, si nécessaire.

TVSDK insère des publicités de la manière suivante :

* **Pré-roll**, qui est placé avant le contenu.
* **Mid-roll**, qui se trouve au milieu du contenu.
* **Post-roll**, qui est placé après le contenu.

>[!TIP]
>
>Une fois la lecture lancée, aucune modification supplémentaire ne peut se produire dans le contenu.

Les publicités ne peuvent pas être :

* Insertion
* Supprimé

  Par exemple, vous ne pouvez pas supprimer des publicités intégrées du contenu pour offrir une expérience sans publicité.
* Remplacé

  Par exemple, vous ne pouvez pas remplacer les publicités intégrées par des publicités ciblées.
