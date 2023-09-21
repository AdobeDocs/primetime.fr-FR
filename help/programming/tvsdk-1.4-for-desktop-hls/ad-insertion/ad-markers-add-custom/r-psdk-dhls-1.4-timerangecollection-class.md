---
description: La classe d’utilitaire TimeRangeCollection abstrait la notion d’une collection ordonnée de spécifications TimeRange et fournit des services pour se traduire en instance de métadonnées.
title: Classe TimeRangeCollection
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Classe TimeRangeCollection{#timerangecollection-class}

La classe d’utilitaire TimeRangeCollection abstrait la notion d’une collection ordonnée de spécifications TimeRange et fournit des services pour se traduire en instance de métadonnées.

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```
public final class TimeRangeCollection { 
    public static const MARK_RANGES:String = "mark_ranges"; 
  
    public function TimeRangeCollection(timeRanges:Vector.<TimeRange>) {…} 
    public function addTimeRange(timeRange:TimeRange):void {…} 
    public function toMetadata(options:Metadata):Metadata {…} 
}
```

Les valeurs définies pour le type de collection sont `MARK_RANGES`, `DELETE_RANGES`, et `REPLACE_RANGES`. Vous pouvez créer `TimeRangeCollection`utilise ces trois types.
