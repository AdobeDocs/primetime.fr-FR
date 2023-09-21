---
description: Les gestionnaires d’événements vous permettent de répondre aux événements TVSDK.
title: Mise en oeuvre des écouteurs d’événement et des rappels
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Mise en oeuvre des écouteurs d’événement et des rappels  {#implement-event-listeners-and-callbacks}

Les gestionnaires d’événements vous permettent de répondre aux événements TVSDK.

Lorsqu’un événement se produit, le mécanisme d’événement de TVSDK appelle votre gestionnaire d’événements enregistré, en lui transmettant les informations d’événement.

TVSDK définit les écouteurs en tant qu’interfaces internes publiques dans `MediaPlayer` .

Votre application doit mettre en oeuvre des écouteurs d’événements pour tout événement TVSDK qui affecte votre application.

1. Déterminez les événements que votre application doit écouter.

   * Événements requis : Prêtez attention à tous les événements de lecture.

     >[!IMPORTANT]
     >
     >Prêtez attention à l’événement de changement d’état qui se produit lorsque l’état du lecteur change d’une manière que vous devez connaître. Les informations qu’il fournit incluent des erreurs qui peuvent affecter les actions suivantes de votre lecteur.

   * Pour d’autres événements, en fonction de votre application, voir  [Résumé des événements du lecteur Primetime](../../android-3x-events-notifications/events-summary/android-3x-events-summary.md).

1. Mettez en oeuvre et ajoutez un écouteur d’événement pour chaque événement.

   Pour la plupart des événements, TVSDK transmet des arguments aux auditeurs d’événement. Ces valeurs fournissent des informations sur l’événement qui peuvent vous aider à décider de la suite. La variable `MediaPlayerEvent` énumération répertorie tous les événements qui `MediaPlayer` dispatches. Pour plus d’informations, voir  [Résumé des événements du lecteur Primetime](../../android-3x-events-notifications/events-summary/android-3x-events-summary.md).

   Par exemple, si `mPlayer` est une instance de `MediaPlayer`, voici comment ajouter et structurer un écouteur d’événement :

   ```java
   mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED, new StatusChangeEventListener() { 
       @Override 
       public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
           event.getMetadata(); 
           if (event.getMetadata() != null) {/* Do something */} 
           if (event.getStatus() == MediaPlayerStatus.IDLE) {/* Do something */} 
           else if (event.getStatus() == MediaPlayerStatus.INITIALIZED) {/* Do something */} 
           else if (event.getStatus() == MediaPlayerStatus.PREPARED) {/* Do something */} 
       } 
   }); 
   ```

## Ordre des événements de lecture {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence attendue.

Les exemples suivants montrent l’ordre de certains événements qui se produisent pendant la lecture.

Lors du chargement réussi d’une ressource multimédia via `MediaPlayer.replaceCurrentResource`, l’ordre des événements est le suivant :

1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZING`

1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZED`

>[!TIP]
>
>Chargez votre ressource multimédia sur le thread principal. Si vous chargez une ressource multimédia sur un thread en arrière-plan, cette opération ou les opérations suivantes peuvent générer une erreur, telle que `MediaPlayerException`, puis quittez .

Lors de la préparation de la lecture `MediaPlayer.prepareToPlay`, l’ordre des événements est le suivant :

1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARING`

1. `MediaPlayerEvent.TIMELINE_UPDATED` si des publicités ont été insérées.
1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARED`

Pour les flux en direct/linéaires, pendant la lecture lorsque la fenêtre de lecture avance et que des opportunités supplémentaires sont résolues, l’ordre des événements est le suivant :

1. `MediaPlayerEvent.ITEM_UPDATED`
1. `MediaPlayerEvent.TIMELINE_UPDATED` si des publicités ont été insérées ;

## Ordre des événements publicitaires {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Lorsque votre lecture comprend de la publicité, TVSDK distribue des événements/notifications dans les séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence attendue.

Lors de la lecture de publicités, l’ordre des événements est le suivant :

* `MediaPlayerEvent.AD_RESOLUTION_COMPLETE`

Les événements suivants sont distribués pour chaque publicité dans la coupure publicitaire :

* `MediaPlayerEvent.AD_BREAK_START`
* `MediaPlayerEvent.AD_START`
* `MediaPlayerEvent.AD_PROGRESS (multiple times)`
* `MediaPlayerEvent.AD_CLICK (for each click)`
* `MediaPlayerEvent.AD_COMPLETE`
* `MediaPlayerEvent.AD_BREAK_COMPLETE`

L’exemple suivant illustre une progression type des événements de lecture de publicité :

```
mediaPlayer.addEventListener(MediaPlayerEvent.AD_RESOLUTION_COMPLETE, new AdResolutionCompleteEventListener() { 
        @Override 
        public void onAdResolutionComplete() { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_BREAK_START, new AdBreakStartedEventListener() { 
         @Override 
        public void onAdBreakStarted(AdBreakPlaybackEvent adBreakPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_START, new AdStartedEventListener() { 
         @Override 
        public void onAdStarted(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_PROGRESS, new AdProgressEventListener() { 
         @Override 
         public void onAdProgress(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_COMPLETE, new AdCompletedEventListener() { 
         @Override 
         public void onAdCompleted(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_BREAK_COMPLETE, new AdBreakCompletedEventListener() { 
         @Override 
         public void onAdBreakCompleted(AdBreakPlaybackEvent adBreakPlaybackEvent) { ... } 
    }); 
 
Below event is for tracking ad clicks. 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_CLICK, new AdClickedEventListener() { 
         @Override 
         public void onAdClicked(AdClickEvent adClickEvent) { ... } 
    });
```

## Ordre des événements DRM {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK distribue des événements DRM (Digital Rights Management, gestion des droits numériques) en réponse aux opérations liées à DRM, comme lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut mettre en oeuvre des actions en réponse à ces événements.

Pour être averti de tous les événements liés à DRM, écoutez `MediaPlayerEvent.DRM_METADATA`. TVSDK distribue des événements DRM supplémentaires par le biais de la fonction `DRMManager` classe .

## Ordre des événements de chargement {#section_5638F8EDACCE422A9425187484D39DCC}

Diffusions TVSDK `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` lorsque des événements de chargement se produisent.
