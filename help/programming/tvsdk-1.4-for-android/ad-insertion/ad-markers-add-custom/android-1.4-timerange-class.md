---
description: Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent les segments de la chronologie.
seo-description: Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent les segments de la chronologie.
seo-title: TimeRange, classe
title: TimeRange, classe
uuid: adf4f1ad-6b3b-48ac-a388-ee1fd54f770b
translation-type: tm+mt
source-git-commit: ''

---


# TimeRange, classe{#timerange-class}

Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent les segments de la chronologie.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Chaque spécification TimeRange de la visionneuse représente un segment de la chronologie de la lecture qui est conservé en interne par TVSDK et qui doit être marqué de manière appropriée comme une période liée à la publicité.

La `TimeRange` classe est une structure de données simple qui expose la position du début et la position finale sur la chronologie. Ces deux propriétés en lecture seule abstraient l’idée d’une plage de temps dans la chronologie de lecture.

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

