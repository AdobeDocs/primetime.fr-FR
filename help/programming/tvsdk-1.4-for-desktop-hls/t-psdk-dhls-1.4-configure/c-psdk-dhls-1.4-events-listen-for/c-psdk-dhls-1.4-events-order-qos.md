---
description: TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’un susceptible d’influencer le calcul des statistiques de QoS, comme la mise en mémoire tampon et la recherche d’un .
seo-description: TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’un susceptible d’influencer le calcul des statistiques de QoS, comme la mise en mémoire tampon et la recherche d’un .
seo-title: ' QoS'
title: ' QoS'
uuid: e6ba1e9b-435b-480d-bea9-bff41b4e0b21
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


#  QoS{#qos-events}

TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’un susceptible d’influencer le calcul des statistiques de QoS, comme la mise en mémoire tampon et la recherche d’un .

L’exemple suivant illustre une progression type de ces  :

```
// For buffering 
mediaPlayer.addEventListener(BufferEvent.BUFFERING_BEGIN, onBufferingBegin); 
private function onBufferingBegin(event:BufferEvent):void { ... } 
 
mediaPlayer.addEventListener(BufferEvent.BUFFERING_END, onBufferingCompleted); 
private function onBufferingCompleted(event:BufferEvent):void { ... } 
 
// For seeking 
mediaPlayer.addEventListener(SeekEvent.SEEK_BEGIN, onSeekBegin); 
private function onSeekBegin(event:SeekEvent):void { ... } 
 
mediaPlayer.addEventListener(SeekEvent.SEEK_COMPLETED, onSeekCompleted); 
private function onSeekCompleted(event:SeekEvent):void { ... } 
 
...  SeekEvent.SEEK_POSITION_ADJUSTED...  //if the desired 
// seek position is modified by the current advertising policies 
```

