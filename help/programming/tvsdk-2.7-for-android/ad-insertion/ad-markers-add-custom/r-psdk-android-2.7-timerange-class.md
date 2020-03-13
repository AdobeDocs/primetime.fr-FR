---
description: Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent des segments de la chronologie.
seo-description: Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent des segments de la chronologie.
seo-title: TimeRange, classe
title: TimeRange, classe
uuid: e5a176af-29b9-4aa6-848e-5aba7988584b
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# TimeRange, classe {#timerange-class}

Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent des segments de la chronologie.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Chaque `TimeRange` spécification de la visionneuse représente un segment sur la chronologie de la lecture qui est conservé en interne par TVSDK et qui doit être correctement marqué comme une période liée à la publicité.

La `TimeRange` classe est une structure de données simple qui expose la position  et la position finale sur le plan de montage chronologique. Ces deux propriétés en lecture seule abstraient l’idée d’une plage de temps dans le plan de montage chronologique de lecture.

>[!TIP]
>
>Les deux valeurs sont exprimées en millisecondes.

Voici un résumé de la `TimeRange` classe :

```java
public final class TimeRange {
    // the start/end values are provided at construction time
    public static TimeRange createRange(long begin, long duration) {...} 

    // only getters are available
    public long getBegin() {...} 
    public long getEnd() {...} 
    public long getDuration() {...}
}
```

