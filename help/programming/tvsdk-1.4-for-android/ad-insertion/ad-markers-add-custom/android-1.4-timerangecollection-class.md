---
description: La classe d'utilitaire TimeRangeCollection abstrait la notion d'une collection ordonnée de spécifications TimeRange et fournit des services pour se traduire en instance de métadonnées.
title: TimeRangeCollection, classe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# TimeRangeCollection, classe{#timerangecollection-class}

La classe d&#39;utilitaire TimeRangeCollection abstrait la notion d&#39;une collection ordonnée de spécifications TimeRange et fournit des services pour se traduire en instance de métadonnées.

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```java
public final class TimeRangeCollection {
    // default constructor method
    public TimeRangeCollection(Type type) {...}

    // the list of timerange specifications provided at construction time 
    public TimeRangeCollection(Type type, List<TimeRange> timeRanges) {...}

    // timerange specs can also be added later
    public void addTimeRange(TimeRange timeRange) {...}

    // translate the set of timerange specs into a Metadata instance 
    public Metadata toMetadata(Metadata options) {...}
}
```

Le paramètre `type`, qui est le premier paramètre de position dans la signature des méthodes du constructeur, est une instance de la énumération `TimeRangeCollection#Type`. Il fait partie de la classe `TimeRangeCollection`. Les valeurs actuellement définies par cette énumération sont `MARK_RANGES`, `DELETE_RANGES` et `REPLACE_RANGES`. Vous pouvez créer des objets `TimeRangeCollection` en utilisant ces trois types.
