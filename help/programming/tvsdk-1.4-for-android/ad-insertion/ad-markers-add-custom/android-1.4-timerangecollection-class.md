---
description: La classe d'utilitaire TimeRangeCollection abstrait la notion d'une collection ordonnée de spécifications TimeRange et fournit des services pour se traduire en instance de métadonnées.
seo-description: La classe d'utilitaire TimeRangeCollection abstrait la notion d'une collection ordonnée de spécifications TimeRange et fournit des services pour se traduire en instance de métadonnées.
seo-title: TimeRangeCollection, classe
title: TimeRangeCollection, classe
uuid: 5705dc9d-4325-44b0-b5aa-196d09c3a67e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

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

Le `type` paramètre, qui est le premier paramètre positionnel dans la signature des méthodes de construction, est une instance de la `TimeRangeCollection#Type` énumération. Ça fait partie de la `TimeRangeCollection` classe. Les valeurs actuellement définies par cette énumération sont `MARK_RANGES`, `DELETE_RANGES`et `REPLACE_RANGES`. Vous pouvez créer `TimeRangeCollection` des objets de ces trois types.
