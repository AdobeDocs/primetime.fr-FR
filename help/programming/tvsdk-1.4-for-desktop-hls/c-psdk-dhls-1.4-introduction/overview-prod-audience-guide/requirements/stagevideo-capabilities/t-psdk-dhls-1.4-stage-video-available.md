---
description: Si StageVideo n’est pas disponible et que votre application tente d’utiliser StageVideo, TVSDK ne génère pas d’erreur. Votre application peut déterminer si StageVideo est disponible en écoutant StageVideoAvailableEvent.
title: Vérifiez si StageVideo est disponible
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# Vérifiez si StageVideo est disponible{#check-whether-stagevideo-is-available}

Si StageVideo n’est pas disponible et que votre application tente d’utiliser StageVideo, TVSDK ne génère pas d’erreur. Votre application peut déterminer si StageVideo est disponible en écoutant StageVideoAvailableEvent.

À partir du Flash 15 et versions ultérieures, lorsque le matériel `StageVideo` n’est pas disponible, il revient au logiciel `StageVideo`. Pour Flash 14 et versions antérieures, vous pouvez déterminer si `StageVideo` est disponible. If `StageVideo` n’est pas disponible, vous pouvez utiliser `StageVideoAvailabilityEvent` pour comprendre pourquoi il n’est pas disponible.

1. Listen for `StageVideoAvailabilityEvent` pour déterminer si `StageVideo` est disponible.

   Par exemple :

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. If `StageVideo` n’est pas disponible, vérifiez `flash.media.StageVideoAvailabilityReason`.
