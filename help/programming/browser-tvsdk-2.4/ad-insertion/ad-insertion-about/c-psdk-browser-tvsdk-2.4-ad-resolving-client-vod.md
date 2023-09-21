---
description: Pour le contenu vidéo à la demande (VOD), le TVSDK du navigateur insère des coupures publicitaires en répliquant les publicités dans le contenu principal afin que la durée de la chronologie augmente.
title: Résoudre et insertion des publicités VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Résoudre et insertion des publicités VOD{#vod-ad-resolving-and-insertion}

Pour le contenu vidéo à la demande (VOD), le TVSDK du navigateur insère des coupures publicitaires en répliquant les publicités dans le contenu principal afin que la durée de la chronologie augmente.

Avant la lecture, le TVSDK du navigateur résout les publicités connues, insère les coupures publicitaires dans le contenu principal, comme décrit par une chronologie renvoyée par la prise de décision publicitaire Adobe Primetime, et recalcule la chronologie virtuelle, si nécessaire.

Le navigateur TVSDK insère les publicités comme suit :

* **Pré-roll**, qui se trouve avant le contenu.
* **Post-roll**, qui se trouve après le contenu.

Une fois la lecture lancée, aucune modification supplémentaire ne peut se produire dans le contenu. Les publicités ne peuvent pas être :

* Insertion
* Supprimé

  Par exemple, vous ne pouvez pas supprimer des publicités intégrées du contenu pour offrir une expérience sans publicité.
* Remplacé

  Par exemple, vous ne pouvez pas remplacer les publicités intégrées par des publicités ciblées.
