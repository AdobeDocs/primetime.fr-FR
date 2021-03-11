---
description: Si StageVideo n’est pas disponible et que votre application tente d’utiliser StageVideo, TVSDK ne génère pas d’erreur. Votre application peut déterminer si StageVideo est disponible en écoutant l’événement StageVideoAvailabilityEvent.
title: Vérifier si StageVideo est disponible
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 1%

---


# Vérifiez si StageVideo est disponible{#check-whether-stagevideo-is-available}

Si StageVideo n’est pas disponible et que votre application tente d’utiliser StageVideo, TVSDK ne génère pas d’erreur. Votre application peut déterminer si StageVideo est disponible en écoutant l’événement StageVideoAvailabilityEvent.

À partir du Flash 15 et des versions ultérieures, lorsque le matériel `StageVideo` n&#39;est pas disponible, il revient au logiciel `StageVideo`. Pour le Flash 14 et les versions antérieures, vous pouvez déterminer si `StageVideo` est disponible. Si `StageVideo` n&#39;est pas disponible, vous pouvez utiliser `StageVideoAvailabilityEvent` pour comprendre pourquoi il n&#39;est pas disponible.

1. Écoutez `StageVideoAvailabilityEvent` pour déterminer si `StageVideo` est disponible.

   Par exemple :

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. Si `StageVideo` n&#39;est pas disponible, vérifiez `flash.media.StageVideoAvailabilityReason`.
