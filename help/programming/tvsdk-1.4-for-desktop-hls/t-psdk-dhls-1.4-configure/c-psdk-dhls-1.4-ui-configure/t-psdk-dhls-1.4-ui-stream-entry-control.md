---
description: Par défaut, lors du démarrage de la lecture, les débuts de médias VOD sont à 0 et les débuts de médias en direct au point de production client (DefaultMediaPlayer.LIVE_POINT).
title: Entrer un flux à un moment donné
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 2%

---


# Entrer un flux à un moment précis{#enter-a-stream-at-a-specific-time}

Par défaut, lors du démarrage de la lecture, les débuts de médias VOD sont à 0 et les débuts de médias en direct au point de production client (DefaultMediaPlayer.LIVE_POINT).

Transmettez une position à `MediaPlayer.prepareToPlay`.

TVSDK considère la position donnée comme le point de départ de la ressource. Aucune opération de recherche n&#39;est requise. Si la position n’est pas comprise dans la plage recherchée, utilise la position par défaut.

Par exemple :

```
var seekableRange:TimeRange=_mediaPlayer.seekableRange; 
if (seekableRange.contains(desiredSeekPosition) { 
    _mediaPlayer.seek(desiredSeekPosition); 
}
```
