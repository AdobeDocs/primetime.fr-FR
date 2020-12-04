---
description: Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent les segments de la chronologie.
seo-description: Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent les segments de la chronologie.
seo-title: TimeRange, classe
title: TimeRange, classe
uuid: 5d0c979e-cc63-4fdd-becc-b0e3987b0891
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# TimeRange class{#timerange-class}

Les marqueurs publicitaires personnalisés vous permettent de transmettre à TVSDK un ensemble de spécifications TimeRange qui représentent les segments de la chronologie.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Chaque spécification `TimeRange` de la visionneuse représente un segment sur la chronologie de la lecture qui est conservé en interne par TVSDK et qui doit être marqué comme une période liée à la publicité.

La classe `TimeRange` est une structure de données simple qui expose la position du début et la position de fin sur la chronologie. Ces deux propriétés en lecture seule abstraient l’idée d’une plage de temps dans la chronologie de lecture.

>[!TIP]
>
>Les deux valeurs sont exprimées en millisecondes.

Voici un résumé de la classe TimeRange :

```
public final class TimeRange {
    // the start/end values are provided at construction 
    public static function createRange(begin:Number, duration:Number {…}
 
    public function get begin():Number {…}
    public function get end():Number {…}
    public function get duration():Number {…}
}
```

