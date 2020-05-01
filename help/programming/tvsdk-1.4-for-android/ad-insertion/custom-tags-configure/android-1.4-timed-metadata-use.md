---
description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.
seo-description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.
seo-title: Utiliser des métadonnées minutées
title: Utiliser des métadonnées minutées
uuid: 98bb8c08-2794-42d6-b5c3-b1047ac804fe
translation-type: tm+mt
source-git-commit: ''

---


# Utiliser des métadonnées minutées {#use-timed-metadata}

Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.

Pour utiliser ces objets enregistrés `TimedMetadata` pendant la lecture, utilisez les objets enregistrés `ArrayList` à partir d’objets [Stocker les métadonnées temporisées au moment de leur distribution](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md).

1. Exécutez un minuteur et requête à plusieurs reprises le temps de lecture actuel.
1. Recherchez tous les `TimedMetadata` objets dont l’heure de début correspond à l’heure de lecture actuelle.

   Vous pouvez utiliser ces objets pour effectuer diverses actions.

[!IMPORTANT]
Lorsque vous vérifiez si le temps de lecture actuel correspond à un `TimedMetadata` objet, incluez `shouldTriggerSubscribedTagEvent` comme condition.

La chronologie peut changer en raison de divers comportements publicitaires. Par exemple, une ou plusieurs coupures publicitaires peuvent être déplacées de leur position d’origine sur le plan de montage chronologique, mais `shouldTriggerSubscribedTagEvent` `TimeMetadata` s’assurent que le début de l’objet correspond au temps de lecture actuel.

Par exemple :

```java
 _playbackClockEventListener = new Clock.ClockEventListener() {
    @Override
    public void onTick(String name) {
        getActivity().runOnUiThread(new Runnable() {
            @Override
            public void run() {
                /* handle timedmetadata object list  */ 
                if (_mediaPlayer != null && _timedMetadataList != null && _timedMetadataList.size() > 0) {
                    if (_lastKnownStatus == MediaPlayer.PlayerState.PLAYING) {
                        long localTime = _mediaPlayer.getLocalTime();
                        Iterator<TimedMetadata> iterator = _timedMetadataList.iterator(); 
                        while (iterator.hasNext()) {
                            TimedMetadata timedMetadata = iterator.next();
                            long diff = localTime - timedMetadata.getTime();
                            if (diff >= 0 &&
                                diff <= PLAYBACK_CLOCK_INTERVAL &&
                                _mediaPlayer.shouldTriggerSubscribedTagEvent()) {
                                // use timed metadata object
                            }
                        }
                    }
                }
            }
        });
    }
};
_playbackClock.addClockEventListener(_playbackClockEventListener);
```

1. Éliminez régulièrement `TimedMetadata` les instances obsolètes de la liste afin d’éviter que la mémoire ne continue à croître.