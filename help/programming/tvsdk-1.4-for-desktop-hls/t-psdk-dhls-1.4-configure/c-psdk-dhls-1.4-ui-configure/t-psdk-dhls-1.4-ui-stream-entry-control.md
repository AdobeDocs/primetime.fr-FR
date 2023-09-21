---
description: Par défaut, lors du démarrage de la lecture, le média VOD démarre à 0 et le média en direct démarre au point d’activation du client (DefaultMediaPlayer.LIVE_POINT).
title: Saisie d’un flux à un moment spécifique
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Saisie d’un flux à un moment spécifique{#enter-a-stream-at-a-specific-time}

Par défaut, lors du démarrage de la lecture, le média VOD démarre à 0 et le média en direct démarre au point d’activation du client (DefaultMediaPlayer.LIVE_POINT).

Transmettre une position à `MediaPlayer.prepareToPlay`.

TVSDK considère la position donnée comme le point de départ de la ressource. Aucune opération de recherche n’est requise. Si la position ne se trouve pas dans la plage pouvant faire l’objet d’une recherche, utilise la position par défaut.

Par exemple :

```
var seekableRange:TimeRange=_mediaPlayer.seekableRange; 
if (seekableRange.contains(desiredSeekPosition) { 
    _mediaPlayer.seek(desiredSeekPosition); 
}
```
