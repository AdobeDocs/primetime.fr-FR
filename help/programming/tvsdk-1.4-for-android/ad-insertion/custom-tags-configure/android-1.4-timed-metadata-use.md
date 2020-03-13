---
description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure de  du.
seo-description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure de  du.
seo-title: Utiliser des métadonnées minutées
title: Utiliser des métadonnées minutées
uuid: 98bb8c08-2794-42d6-b5c3-b1047ac804fe
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Utiliser des métadonnées minutées {#use-timed-metadata}

Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure de  du.

Pour utiliser ces `TimedMetadata` objets enregistrés pendant la lecture, utilisez les objets enregistrés `ArrayList` à partir des métadonnées temporisées du [magasin au moment où ils sont distribués](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md).

1. Exécutez un minuteur et à plusieurs reprises le temps de lecture actuel.
1. Recherchez tous les `TimedMetadata` objets dont l’heure de  est et qui correspondent à l’heure de lecture actuelle.

   Vous pouvez utiliser ces objets pour effectuer diverses actions.

[!IMPORTANT]
Lorsque vous vérifiez si le temps de lecture actuel correspond à un `TimedMetadata` objet, incluez `shouldTriggerSubscribedTagEvent` comme condition.

La chronologie peut changer en raison de divers comportements publicitaires. Par exemple, une ou plusieurs coupures publicitaires peuvent être déplacées de leur position d’origine sur le plan de montage chronologique, mais `shouldTriggerSubscribedTagEvent` garantissent que l’heure de  de l’ `TimeMetadata` objet correspond à l’heure de lecture actuelle.

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

1. Videz régulièrement `TimedMetadata` les instances obsolètes du pour éviter que la mémoire ne continue à croître.