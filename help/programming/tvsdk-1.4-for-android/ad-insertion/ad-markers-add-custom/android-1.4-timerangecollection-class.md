---
description: La classe d’utilitaire TimeRangeCollection abstrait la notion d’une collection ordonnée de spécifications TimeRange et fournit des services pour se traduire en instance de métadonnées.
title: Classe TimeRangeCollection
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Classe TimeRangeCollection{#timerangecollection-class}

La classe d’utilitaire TimeRangeCollection abstrait la notion d’une collection ordonnée de spécifications TimeRange et fournit des services pour se traduire en instance de métadonnées.

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

La variable `type` , qui est le premier paramètre de position dans la signature des méthodes du constructeur, est une instance de la propriété `TimeRangeCollection#Type` énumération. Cela fait partie de la `TimeRangeCollection` classe . Les valeurs actuellement définies par cette énumération sont `MARK_RANGES`, `DELETE_RANGES`, et `REPLACE_RANGES`. Vous pouvez créer `TimeRangeCollection` en utilisant ces trois types d’objets.
