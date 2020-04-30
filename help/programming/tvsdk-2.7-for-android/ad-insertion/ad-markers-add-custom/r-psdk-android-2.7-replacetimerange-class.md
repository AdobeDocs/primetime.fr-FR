---
description: La classe d'utilitaire ReplaceTimeRange est une extension de la classe TimeRange à utiliser avec CustomRangeMetadata.
seo-description: La classe d'utilitaire ReplaceTimeRange est une extension de la classe TimeRange à utiliser avec CustomRangeMetadata.
seo-title: ReplaceTimeRange, classe
title: ReplaceTimeRange, classe
uuid: 19c49b26-5096-4429-b30b-bdd2502e3036
translation-type: tm+mt
source-git-commit: ''

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

