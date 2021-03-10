---
description: 'L’interface com.adobe.mediacore.timeline.TimelineMarker contient désormais une nouvelle méthode. '
title: 'Mise à niveau de la version 2.5.x des annonces avec mise en page résolue vers la version 3.0.0 Résolution des publicités avec mise en page avec mise en page différée (modifications d’API/flux de travail) '
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# Mise à niveau de la version 2.5.x Résoudre les publicités diffuses vers la version 3.x Résolution des publicités diffuses (modifications d’API/flux de travail) :{#upgrading-from-x-lazy-ad-resolving-to-lazy-ad-resolving-api-workflow-changes}

L’interface com.adobe.mediacore.timeline.TimelineMarker contient désormais une nouvelle méthode :

**Placement.Type getPlacementType()**

Cette méthode renvoie un type de placement de Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL ou Placement.Type.POST_ROLL. Si une coupure publicitaire n’est pas résolue, la méthode `getDuration()`sur l’interface TimelineMarker renvoie 0.

>[!NOTE]
>
>Cette interface n’est pas toujours transmise dans le type com.mediacore.timeline.publicités.AdBreakTimelineItem si elle n’a pas encore été résolue. Il sera possible de le caster si la méthode `getDuration()` de TimelineMarker est supérieure à 0.

**Modifications du événement :**

`kEventAdResolutionComplete` est maintenant amorti et est maintenant déclenché immédiatement après que le joueur ait atteint l’état PRÉPARÉ. Les applications qui n&#39;écoutaient auparavant que ce événement pour dessiner la barre de défilement devraient changer cela pour écouter `kEventTimelineUpdated` uniquement. Une fois les coupures publicitaires individuelles résolues, un nouveau événement `kEventTimelineUpdated` est distribué.
