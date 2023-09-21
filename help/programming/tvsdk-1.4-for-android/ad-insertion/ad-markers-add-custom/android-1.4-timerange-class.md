---
description: Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent les segments de la chronologie.
title: Classe TimeRange
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Classe TimeRange{#timerange-class}

Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent les segments de la chronologie.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Chaque spécification TimeRange de la visionneuse représente un segment de la chronologie de lecture qui est conservé en interne par TVSDK et qui doit être marqué de manière appropriée comme une période liée aux publicités.

La variable `TimeRange` est une structure de données simple qui expose la position de début et la position de fin sur la chronologie. Ces deux propriétés en lecture seule abstraient l’idée d’une période dans la chronologie de lecture.

>[!TIP]
>
>Les deux valeurs sont exprimées en millisecondes.

Voici un résumé de la `TimeRange` Classe :

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
