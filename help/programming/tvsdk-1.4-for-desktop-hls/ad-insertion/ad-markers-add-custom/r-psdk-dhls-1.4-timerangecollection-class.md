---
description: La classe d'utilitaire TimeRangeCollection abstrait la notion d'une collection ordonnée de spécifications TimeRange et fournit des services pour se traduire en instance de métadonnées.
title: TimeRangeCollection, classe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 0%

---


# TimeRangeCollection, classe{#timerangecollection-class}

La classe d&#39;utilitaire TimeRangeCollection abstrait la notion d&#39;une collection ordonnée de spécifications TimeRange et fournit des services pour se traduire en instance de métadonnées.

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```
public final class TimeRangeCollection { 
    public static const MARK_RANGES:String = "mark_ranges"; 
  
    public function TimeRangeCollection(timeRanges:Vector.<TimeRange>) {…} 
    public function addTimeRange(timeRange:TimeRange):void {…} 
    public function toMetadata(options:Metadata):Metadata {…} 
}
```

La valeur définie pour le type de collection est `MARK_RANGES`, `DELETE_RANGES` et `REPLACE_RANGES`. Vous pouvez créer des `TimeRangeCollection`s à l&#39;aide de ces trois types.
