---
description: 'L’interface com.adobe.mediacore.timeline.TimelineMarker contient désormais une nouvelle méthode. '
seo-description: 'L’interface com.adobe.mediacore.timeline.TimelineMarker contient désormais une nouvelle méthode. '
seo-title: 'Mise à niveau de la version 2.5.x des annonces avec mise en page résolue vers la version 3.0.0 Résolution des publicités avec mise en page avec mise en page différée (modifications d’API/flux de travail) '
title: 'Mise à niveau de la version 2.5.x des annonces avec mise en page résolue vers la version 3.0.0 Résolution des publicités avec mise en page avec mise en page différée (modifications d’API/flux de travail) '
uuid: 5870ceb4-93a8-4c8b-b716-673396122644
translation-type: tm+mt
source-git-commit: ''

---


# Mise à niveau de la version 2.5.x Résoudre les publicités diffuses vers la version 3.x Résolution des publicités diffuses (modifications d’API/flux de travail) :{#upgrading-from-x-lazy-ad-resolving-to-lazy-ad-resolving-api-workflow-changes}

L’interface com.adobe.mediacore.timeline.TimelineMarker contient désormais une nouvelle méthode :

**Placement.Type getPlacementType()**

Cette méthode renvoie un type de placement de Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL ou Placement.Type.POST_ROLL. Si une coupure publicitaire n’est pas résolue, la `getDuration()`méthode de l’interface TimelineMarker renvoie 0.

>[!NOTE]
>
>Cette interface n’est pas toujours transmise dans le type com.mediacore.timeline.publicités.AdBreakTimelineItem si elle n’a pas encore été résolue. Il sera possible de le caster si la `getDuration()` méthode de TimelineMarker est supérieure à 0.

**Modifications du Événement :**

`kEventAdResolutionComplete` est maintenant amorti et est maintenant déclenché immédiatement après que le joueur ait atteint l’état PRÉPARÉ. Les applications qui n&#39;écoutaient auparavant que ce événement pour dessiner la barre de défilement devraient changer ceci pour écouter `kEventTimelineUpdated` seulement. Une fois les coupures publicitaires individuelles résolues, un nouveau `kEventTimelineUpdated` événement est distribué.
