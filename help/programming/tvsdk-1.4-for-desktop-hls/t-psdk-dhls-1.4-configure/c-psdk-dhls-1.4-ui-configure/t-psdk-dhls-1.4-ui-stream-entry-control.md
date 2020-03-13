---
description: Par défaut, lors du démarrage de la lecture, le de médias VOD  à 0 et le de médias en direct  au point d’accès client (DefaultMediaPlayer.LIVE_POINT).
seo-description: Par défaut, lors du démarrage de la lecture, le de médias VOD  à 0 et le de médias en direct  au point d’accès client (DefaultMediaPlayer.LIVE_POINT).
seo-title: Entrer un flux à un moment spécifique
title: Entrer un flux à un moment spécifique
uuid: f58d908a-77b9-465f-b3a9-8fe63a249d39
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Entrer un flux à un moment spécifique{#enter-a-stream-at-a-specific-time}

Par défaut, lors du démarrage de la lecture, le de médias VOD  à 0 et le de médias en direct  au point d’accès client (DefaultMediaPlayer.LIVE_POINT).

Passe une position à `MediaPlayer.prepareToPlay`.

TVSDK considère la position donnée comme le point de départ de la ressource. Aucune opération de recherche n’est requise. Si la position n’est pas comprise dans la plage recherchée, utilise la position par défaut.

Par exemple :

```
var seekableRange:TimeRange=_mediaPlayer.seekableRange; 
if (seekableRange.contains(desiredSeekPosition) { 
    _mediaPlayer.seek(desiredSeekPosition); 
}
```
