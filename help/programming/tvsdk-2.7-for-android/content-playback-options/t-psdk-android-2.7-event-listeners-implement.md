---
description: Les gestionnaires de Événements vous permettent de répondre aux événements TVSDK.
seo-description: Les gestionnaires de Événements vous permettent de répondre aux événements TVSDK.
seo-title: Mise en oeuvre des écouteurs et des rappels de événement
title: Mise en oeuvre des écouteurs et des rappels de événement
uuid: bb1980f3-340b-4d36-ae7e-c9fc1d145233
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Mise en oeuvre des écouteurs et des rappels de événement {#implement-event-listeners-and-callbacks}

Les gestionnaires de Événements vous permettent de répondre aux événements TVSDK.

Lorsqu&#39;un événement se produit, le mécanisme de événement de TVSDK appelle votre gestionnaire de événements enregistré, en lui transmettant les informations du événement.

TVSDK définit les écouteurs comme des interfaces internes publiques à l’intérieur de l’ `MediaPlayer` interface.

Votre application doit mettre en oeuvre des écouteurs de événement pour tous les événements TVSDK qui affectent votre application.

1. Déterminez quels événements votre application doit écouter.

   * événements requis : Prêtez attention à tous les événements de lecture.

      >[!IMPORTANT]
      >
      >Prêtez attention au événement de changement d’état qui se produit lorsque l’état du lecteur change d’une manière que vous devez connaître. Les informations qu’il fournit incluent des erreurs qui peuvent affecter les actions futures de votre lecteur.

   * Pour les autres événements, en fonction de votre application, voir événements-summary .

1. Implémentez et ajoutez un écouteur de événement pour chaque événement.

   >[!NOTE]
   >
   >Pour la plupart des événements, TVSDK transmet les arguments aux auditeurs du événement. Ces valeurs fournissent des informations sur le événement qui peuvent vous aider à décider de la suite à donner. La `MediaPlayerEvent` énumération liste tous les événements qui `MediaPlayer` sont distribués. Pour plus d’informations, voir événements-récapitulatifs .

   Par exemple, si `mPlayer` est une instance de `MediaPlayer`, voici comment vous pouvez ajouter et structurer un écouteur de événement :

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

TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions en fonction des événements de la séquence prévue.

Les exemples suivants montrent l’ordre de certains événements survenant pendant la lecture.

Lors du chargement réussi d&#39;une ressource multimédia par `MediaPlayer.replaceCurrentResource`l&#39;intermédiaire de, l&#39;ordre des événements est le suivant :

1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZING`

1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZED`

>[!TIP]
>
>Chargez votre ressource multimédia sur le thread principal. Si vous chargez une ressource multimédia sur un thread en arrière-plan, cette opération ou les opérations suivantes peuvent générer une erreur, telle que `MediaPlayerException`et quitter.

Lors de la préparation de la lecture à travers `MediaPlayer.prepareToPlay`la vidéo, l’ordre des événements est le suivant :

1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARING`

1. `MediaPlayerEvent.TIMELINE_UPDATED` si des publicités ont été insérées.
1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARED`

Pour les flux en direct/linéaires, pendant la lecture, à mesure que la fenêtre de lecture avance et que des opportunités supplémentaires sont résolues, l’ordre des événements est le suivant :

1. `MediaPlayerEvent.ITEM_UPDATED`
1. `MediaPlayerEvent.TIMELINE_UPDATED` si des publicités ont été insérées

## Ordre des événements publicitaires {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Lorsque la lecture comprend de la publicité, TVSDK envoie des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence prévue.

Lors de la lecture des publicités, l’ordre des événements est le suivant :

* `MediaPlayerEvent.AD_RESOLUTION_COMPLETE`

Les événements suivants sont distribués pour chaque publicité au cours de la coupure publicitaire :

* `MediaPlayerEvent.AD_BREAK_START`
* `MediaPlayerEvent.AD_START`
* `MediaPlayerEvent.AD_PROGRESS (multiple times)`
* `MediaPlayerEvent.AD_CLICK (for each click)`
* `MediaPlayerEvent.AD_COMPLETE`
* `MediaPlayerEvent.AD_BREAK_COMPLETE`

L’exemple suivant montre une progression type des événements de lecture publicitaire :

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

TVSDK distribue des événements de gestion des droits numériques (DRM) en réponse à des opérations liées à la gestion des droits numériques, par exemple lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut implémenter des actions en réponse à ces événements.

Pour être averti de tous les événements liés à la gestion des droits numériques, écoutez `MediaPlayerEvent.DRM_METADATA`. TVSDK distribue d’autres événements DRM par l’intermédiaire de la `DRMManager` classe.

## Ordre des événements du chargeur {#section_5638F8EDACCE422A9425187484D39DCC}

TVSDK distribue des messages `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` lorsque des événements de chargeur se produisent.