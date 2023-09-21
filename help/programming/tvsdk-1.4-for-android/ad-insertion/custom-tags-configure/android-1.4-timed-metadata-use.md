---
description: Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure de début.
title: Utilisation de métadonnées minutées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Utilisation de métadonnées minutées {#use-timed-metadata}

Vous pouvez utiliser TimedMetadata lorsque l’heure de lecture actuelle correspond à l’heure de début.

Pour les utiliser `TimedMetadata` pendant la lecture, utilisez l’objet enregistré `ArrayList` de [Stocker les objets de métadonnées minutées lors de leur distribution](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md).

1. Exécutez un minuteur et effectuez à plusieurs reprises une requête sur la durée de lecture actuelle.
1. Recherchez l’ensemble des `TimedMetadata` avec les heures de début correspondant à l’heure de lecture actuelle.

   Vous pouvez utiliser ces objets pour effectuer diverses actions.

   >[!IMPORTANT]
   >
   >Lorsque vous vérifiez si l’heure de lecture actuelle correspond à l’une des valeurs `TimedMetadata` objets, inclure `shouldTriggerSubscribedTagEvent` comme condition.

   La chronologie peut changer en raison de divers comportements publicitaires. Par exemple, une ou plusieurs coupures publicitaires peuvent être déplacées de leur position d’origine dans la chronologie, mais `shouldTriggerSubscribedTagEvent` s’assure que la variable `TimeMetadata` l’heure de début de l’objet correspond à l’heure de lecture actuelle.

   Par exemple :

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

1. Périodique de vidage `TimedMetadata` des instances de la liste pour empêcher la mémoire de croître en continu.
