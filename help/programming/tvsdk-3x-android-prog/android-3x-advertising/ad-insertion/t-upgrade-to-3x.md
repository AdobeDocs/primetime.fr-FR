---
description: L’interface com.adobe.mediacore.timeline.TimelineMarker contient désormais une nouvelle méthode.
title: Mise à niveau de la version 2.5.x des publicités différées vers la version 3.0.0 Résolution des publicités différées (modifications API/workflow)
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Mise à niveau de la version 2.5.x des publicités différées vers la version 3.x Résolution des publicités différées (modifications API/workflow) :{#upgrading-from-x-lazy-ad-resolving-to-lazy-ad-resolving-api-workflow-changes}

L’interface com.adobe.mediacore.timeline.TimelineMarker contient désormais une nouvelle méthode :

**Placement.Type getPlacementType()**

Cette méthode renvoie un type d’emplacement de Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL ou Placement.Type.POST_ROLL. Si une coupure publicitaire n’est pas résolue, la variable `getDuration()`sur l’interface TimelineMarker renvoie 0.

>[!NOTE]
>
>Cette interface n’est pas toujours placée dans le type com.mediacore.timeline.advertising.AdBreakTimelineItem si elle n’a pas encore été résolue. Elle pourra être diffusée si la variable `getDuration()` de TimelineMarker est supérieure à 0.

**Modifications des événements :**

`kEventAdResolutionComplete` est désormais déprécié et est désormais déclenché immédiatement une fois que le lecteur a atteint l’état PRÉPARÉ . Les applications qui écoutaient auparavant uniquement cet événement pour dessiner la barre de défilement doivent la modifier pour écouter `kEventTimelineUpdated` uniquement. Une fois les coupures publicitaires individuelles résolues, une nouvelle `kEventTimelineUpdated` sera distribué.
