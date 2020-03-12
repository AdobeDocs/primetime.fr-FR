---
description: Les gestionnaires de  de vous permettent de répondre aux  de TVSDK.
seo-description: Les gestionnaires de  de vous permettent de répondre aux  de TVSDK.
seo-title: 'Mise en oeuvre des écouteurs et des rappels de '
title: 'Mise en oeuvre des écouteurs et des rappels de '
uuid: bb1980f3-340b-4d36-ae7e-c9fc1d145233
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Mise en oeuvre des écouteurs et des rappels de {#implement-event-listeners-and-callbacks}

Les gestionnaires de  de vous permettent de répondre aux  de TVSDK.

Lorsqu&#39;un se produit, le mécanisme de  de TVSDK appelle votre gestionnaire de enregistré, lui transmettant les informations de l&#39;.

TVSDK définit les écouteurs comme des interfaces internes publiques dans l’ `MediaPlayer` interface.

Votre application doit mettre en oeuvre des écouteurs de  pour tout TVSDK  qui affecte votre application.

1. Déterminez quel  votre application doit écouter.

   *  de requis : Écoute tous les  de lecture.

      >[!IMPORTANT]
      >
      >Prêtez attention au  de changement d’état, qui se produit lorsque l’état du lecteur change d’une manière que vous devez connaître. Les informations qu’il fournit incluent des erreurs qui peuvent affecter les actions de votre lecteur.

   * Pour les autres , selon votre application, voir -summary .

1. Implémentez et ajoutez un écouteur de  pour chaque  de.

   >[!NOTE]
   >
   >Pour la plupart des,  TVSDK transmet les arguments aux auditeurs . Ces valeurs fournissent des informations sur le  du qui peuvent vous aider à décider de ce que vous devez faire ensuite. Le `MediaPlayerEvent`  tout le  qui `MediaPlayer` envoie. Pour plus d&#39;informations, reportez-vous à la -synthèse des .

   Par exemple, si `mPlayer` est une instance de `MediaPlayer`, voici comment vous pouvez ajouter et structurer un écouteur de  :

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

## Ordre du de lecture {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.

Les exemples suivants montrent l’ordre de certains  qui se produisent pendant la lecture.

Lors du chargement réussi d’une ressource multimédia via `MediaPlayer.replaceCurrentResource`, l’ordre des  est le suivant :

1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZING`

1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.INITIALIZED`

>[!TIP]
>
>Chargez votre ressource multimédia sur le thread principal. Si vous chargez une ressource multimédia sur un thread d’arrière-plan, cette opération ou les opérations suivantes peuvent renvoyer une erreur, telle que `MediaPlayerException`et quitter.

Lors de la préparation de la lecture `MediaPlayer.prepareToPlay`, l’ordre des  est le suivant :

1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARING`

1. `MediaPlayerEvent.TIMELINE_UPDATED` si des publicités ont été insérées.
1. `MediaPlayerEvent.STATUS_CHANGED` avec état `MediaPlayerStatus.PREPARED`

Pour les flux en direct/linéaires, pendant la lecture au fur et à mesure que la fenêtre de lecture avance et que des opportunités supplémentaires sont résolues, l’ordre des  est le suivant :

1. `MediaPlayerEvent.ITEM_UPDATED`
1. `MediaPlayerEvent.TIMELINE_UPDATED` si des publicités ont été insérées

## Ordre des publicitaires {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Lorsque votre lecture comprend de la publicité, TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut implémenter des actions basées sur des  dans la séquence prévue.

Lors de la lecture des publicités, l’ordre des  est le suivant :

* `MediaPlayerEvent.AD_RESOLUTION_COMPLETE`

Les  suivantes sont distribuées pour chaque publicité durant la coupure publicitaire :

* `MediaPlayerEvent.AD_BREAK_START`
* `MediaPlayerEvent.AD_START`
* `MediaPlayerEvent.AD_PROGRESS (multiple times)`
* `MediaPlayerEvent.AD_CLICK (for each click)`
* `MediaPlayerEvent.AD_COMPLETE`
* `MediaPlayerEvent.AD_BREAK_COMPLETE`

L’exemple suivant illustre une progression type du de lecture d’annonce :

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

## Ordre du DRM {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut implémenter des actions en réponse à ces  de.

Pour être informé de tous les  de DRM, écoutez `MediaPlayerEvent.DRM_METADATA`. TVSDK distribue des DRM supplémentaires par l’intermédiaire de la `DRMManager` classe.

## Ordre du de chargeur {#section_5638F8EDACCE422A9425187484D39DCC}

TVSDK est distribué `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` lorsque le de chargeur se produit.