---
description: La classe d'utilitaire ReplaceTimeRange est une extension de la classe TimeRange à utiliser avec CustomRangeMetadata.
seo-description: La classe d'utilitaire ReplaceTimeRange est une extension de la classe TimeRange à utiliser avec CustomRangeMetadata.
seo-title: ReplaceTimeRange, classe
title: ReplaceTimeRange, classe
uuid: d554c17a-2bdc-4c4a-bb8f-2d357511bb32
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# ReplaceTimeRange, classe {#replacetimerange-class}

La classe d&#39;utilitaire ReplaceTimeRange est une extension de la classe TimeRange à utiliser avec CustomRangeMetadata.

```java
public class ReplaceTimeRange extends TimeRange {
    // Default constructor method
    public ReplaceTimeRange() { 
        ... 
    }

    // Details of begining, duration and replaceDuration 
    // provided at construction time 
    public ReplaceTimeRange(long begin, long duration, long replaceDuration) { 
        ... 
    }

    // Replace duration
    public long getReplaceDuration() { 
        ... 
    }
}
```
