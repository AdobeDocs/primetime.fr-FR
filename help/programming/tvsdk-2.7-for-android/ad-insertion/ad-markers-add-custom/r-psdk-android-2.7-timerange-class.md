---
description: Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent les segments de la chronologie.
title: TimeRange, classe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# TimeRange, classe {#timerange-class}

Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent les segments de la chronologie.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Chaque spécification `TimeRange` de la visionneuse représente un segment sur la chronologie de la lecture qui est conservé en interne par TVSDK et qui doit être marqué comme une période liée à la publicité.

La classe `TimeRange` est une structure de données simple qui expose la position du début et la position de fin sur la chronologie. Ces deux propriétés en lecture seule abstraient l’idée d’une plage de temps dans la chronologie de lecture.

>[!TIP]
>
>Les deux valeurs sont exprimées en millisecondes.

Voici un résumé de la classe `TimeRange` :

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

