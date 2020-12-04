---
description: Si StageVideo n’est pas disponible et que votre application tente d’utiliser StageVideo, TVSDK ne génère pas d’erreur. Votre application peut déterminer si StageVideo est disponible en écoutant l’événement StageVideoAvailabilityEvent.
seo-description: Si StageVideo n’est pas disponible et que votre application tente d’utiliser StageVideo, TVSDK ne génère pas d’erreur. Votre application peut déterminer si StageVideo est disponible en écoutant l’événement StageVideoAvailabilityEvent.
seo-title: Vérifier si StageVideo est disponible
title: Vérifier si StageVideo est disponible
uuid: 09c39442-cb9a-4892-af99-3d3d9bf1d4a7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '160'
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
