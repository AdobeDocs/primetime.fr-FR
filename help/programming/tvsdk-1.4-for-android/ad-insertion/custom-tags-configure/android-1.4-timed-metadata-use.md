---
description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.
seo-description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.
seo-title: Utiliser des métadonnées minutées
title: Utiliser des métadonnées minutées
uuid: 98bb8c08-2794-42d6-b5c3-b1047ac804fe
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 1%

---


# Utiliser des métadonnées minutées {#use-timed-metadata}

Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure du début.

Pour utiliser ces objets `TimedMetadata` enregistrés au cours de la lecture, utilisez les `ArrayList` enregistrés de [Stocker les objets de métadonnées minutées au fur et à mesure qu&#39;ils sont distribués](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md).

1. Exécutez un minuteur et requête à plusieurs reprises le temps de lecture actuel.
1. Recherchez tous les objets `TimedMetadata` dont les heures de début correspondent à l’heure de lecture actuelle.

   Vous pouvez utiliser ces objets pour effectuer diverses actions.

   >[!IMPORTANT]
   >
   >Lorsque vous vérifiez si l’heure de lecture actuelle correspond à un objet `TimedMetadata`, incluez `shouldTriggerSubscribedTagEvent` comme condition.

   La chronologie peut changer en raison de divers comportements publicitaires. Par exemple, une ou plusieurs coupures publicitaires peuvent être déplacées de leur position d’origine sur la chronologie, mais `shouldTriggerSubscribedTagEvent` s’assure que l’heure de début de l’objet `TimeMetadata` correspond à l’heure de lecture actuelle.

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

1. Éliminez régulièrement les instances `TimedMetadata` obsolètes de la liste afin d’éviter que la mémoire ne continue à croître.