---
description: Si StageVideo n’est pas disponible et que votre application tente d’utiliser StageVideo, TVSDK ne génère pas d’erreur. Votre application peut déterminer si StageVideo est disponible en écoutant l’événement StageVideoAvailabilityEvent.
seo-description: Si StageVideo n’est pas disponible et que votre application tente d’utiliser StageVideo, TVSDK ne génère pas d’erreur. Votre application peut déterminer si StageVideo est disponible en écoutant l’événement StageVideoAvailabilityEvent.
seo-title: Vérifier si StageVideo est disponible
title: Vérifier si StageVideo est disponible
uuid: 09c39442-cb9a-4892-af99-3d3d9bf1d4a7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Vérifier si StageVideo est disponible{#check-whether-stagevideo-is-available}

Si StageVideo n’est pas disponible et que votre application tente d’utiliser StageVideo, TVSDK ne génère pas d’erreur. Votre application peut déterminer si StageVideo est disponible en écoutant l’événement StageVideoAvailabilityEvent.

A partir de Flash 15 et des versions ultérieures, lorsque le matériel `StageVideo` n&#39;est pas disponible, il revient au logiciel `StageVideo`. Pour Flash 14 et les versions antérieures, vous pouvez déterminer s’ `StageVideo` il est disponible. Si `StageVideo` n’est pas disponible, vous pouvez `StageVideoAvailabilityEvent` comprendre pourquoi il n’est pas disponible.

1. Prêtez attention `StageVideoAvailabilityEvent` à déterminer si `StageVideo` est disponible.

   Par exemple :

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. Si `StageVideo` n&#39;est pas disponible, cochez `flash.media.StageVideoAvailabilityReason`.
