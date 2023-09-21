---
description: Les gestionnaires d’événements permettent à TVSDK de répondre aux événements.
title: Mise en oeuvre des écouteurs d’événement et des rappels
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Mise en oeuvre des écouteurs d’événement et des rappels{#implement-event-listeners-and-callbacks}

Les gestionnaires d’événements permettent à TVSDK de répondre aux événements.

Lorsqu’un événement se produit, le mécanisme d’événement de TVSDK appelle votre gestionnaire d’événements enregistré et transmet les informations d’événement au gestionnaire.

TVSDK définit les écouteurs comme des interfaces internes publiques dans `MediaPlayer` .

Votre application doit mettre en oeuvre des écouteurs d’événements pour les événements TVSDK qui affectent votre application.

Pour obtenir la liste complète des événements d’analyse vidéo, voir Suivi de la lecture vidéo principale.

1. Déterminez les événements que votre application doit écouter.

   * **Événements requis**: écoute tous les événements de lecture.

     >[!IMPORTANT]
     >
     >Événement de lecture `onStateChanged` fournit l’état du lecteur, y compris les erreurs. L’un des états peut affecter l’étape suivante du lecteur.

   * **Autres événements**: facultatif, selon votre application.

     Par exemple, si vous incorporez de la publicité dans votre lecture, implémentez les rappels AdPlaybackEventListener .

1. Mettez en oeuvre des écouteurs d’événement pour chaque événement.

   TVSDK renvoie des valeurs de paramètre à vos rappels d’écouteurs d’événements. Ces valeurs fournissent des informations pertinentes sur l’événement que vous pouvez utiliser dans vos écouteurs pour effectuer les actions appropriées.

   `MediaPlayer.EventListener` répertorie toutes les interfaces de rappel. Chaque interface affiche le nom du rappel et les paramètres renvoyés pour chaque événement.

   Par exemple :

   ```
   MediaPlayer.PlaybackEventListener.onStateChanged( 
    MediaPlayer.PlayerState state, MediaPlayerNotification notification)
   ```

1. Enregistrez vos écouteurs de rappel avec l’événement `MediaPlayer` en utilisant `MediaPlayer.addEventListener`.

   ```
   mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, 
    new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onStateChanged( 
    MediaPlayer.PlayerState state, 
    MediaPlayerNotification notification) {...} 
   }
   ```

## Ordre des événements de lecture {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK distribue des événements/notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence attendue.

Les exemples suivants montrent l’ordre de certains événements qui incluent des événements de lecture.

* Lors du chargement réussi d’une ressource multimédia via `MediaPlayer.replaceCurrentResource`, l’ordre des événements est le suivant :

1. `MediaPlayer.PlaybackEventListener.onStateChanged` avec état `MediaPlayer.PlayerState.INITIALIZING`

1. `MediaPlayer.PlaybackEventListener.onStateChanged` avec état `MediaPlayer.PlayerState.INITIALIZED`

>[!TIP]
>
>Chargez votre ressource multimédia sur le thread principal. Si vous chargez une ressource multimédia sur un thread d’arrière-plan, cette opération ou les opérations TVSDK suivantes, ou les deux, peuvent générer une erreur (par exemple, `IllegalStateException`) et de quitter.

* Lors de la préparation de la lecture `MediaPlayer.prepareToPlay`, l’ordre des événements est le suivant :

1. `MediaPlayer.PlaybackEventListener.onStateChanged` avec état `MediaPlayerStatus.PREPARING`

1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` si des publicités ont été insérées.
1. `MediaPlayer.PlaybackEventListener.onStateChanged` avec état `MediaPlayerStatus.PREPARED`

* Pour les flux en direct/linéaires, pendant la lecture lorsque la fenêtre de lecture avance et que des opportunités supplémentaires sont résolues, l’ordre des événements est le suivant :

1. `MediaPlayer.PlaybackEventListener.onUpdated`
1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` si des publicités ont été insérées ;
1. `MediaPlayerItemEvent.ITEM_UPDATED`
1. `TimelineEvent.TIMELINE_UPDATED` si des publicités ont été insérées ;

L’exemple suivant illustre une progression type d’événements :

```java
mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK,  
  new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() {...} 
    @Override 
    public void onUpdated() {...} 
    @Override 
    public void onPlayStart() {...} 
    @Override 
    public void onPlayComplete() {...} 
    @Override 
    public void onSizeAvailable(long height, long width) {...} 
    @Override 
    public void onStateChanged(MediaPlayer.PlayerState state,  
      MediaPlayerNotification notification) {...} 
});
```

## Ordre des événements publicitaires {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Lorsque votre lecture comprend de la publicité, TVSDK distribue des événements/notifications dans les séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des événements dans la séquence attendue.

Lors de la lecture de publicités, l’ordre des événements est le suivant :

* `AdPlaybackEventListener.onAdBreakStart`
* Les éléments suivants sont distribués pour chaque publicité dans la coupure publicitaire :

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` (plusieurs fois pendant la lecture d’une publicité)
   * `AdPlaybackEventListener.onAdClick` (pour chaque clic)
   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdBreakComplete`

L’exemple suivant illustre une progression type des événements de lecture de publicité :

```java
mediaPlayer.addEventListener(MediaPlayer.Event.AD_PLAYBACK,  
  new MediaPlayer.AdPlaybackEventListener() { 
    @Override  
    public void onAdBreakStart(AdBreak adBreak) { ... } 
    @Override 
    public void onAdStart(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdProgress(AdBreak adBreak, Ad ad, int percentage) { ... }  
    @Override 
    public void onAdComplete(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdBreakComplete(AdBreak adBreak) { ... } 
    @Override 
    public void onAdClick(AdBreak adBreak, Ad ad, AdClick adClick) { ... } 
});
```

Lors de la lecture de publicités, l’ordre des événements est le suivant :

* `AdPlaybackEventListener.onAdBreakStart`
* Les éléments suivants sont distribués pour chaque publicité dans la coupure publicitaire :

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` (plusieurs fois pendant la lecture d’une publicité)
   * `AdPlaybackEventListener.onAdClick` (pour chaque clic)
   * `AdPlaybackEventListener.onAdStart`

* `AdPlaybackEventListener.onAdBreakComplete`

L’exemple suivant illustre une progression type des événements de lecture de publicité :

```java
mediaPlayer.addEventListener(MediaPlayer.Event.AD_PLAYBACK,  
  new MediaPlayer.AdPlaybackEventListener() { 
    @Override  
    public void onAdBreakStart(AdBreak adBreak) { ... } 
    @Override 
    public void onAdStart(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdProgress(AdBreak adBreak, Ad ad, int percentage) { ... }  
    @Override 
    public void onAdComplete(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdBreakComplete(AdBreak adBreak) { ... } 
    @Override 
    public void onAdClick(AdBreak adBreak, Ad ad, AdClick adClick) { ... } 
});
```

## Événements QoS {#section_9BFF3CD7AA1C4BD6960ACF6B9C0B25CC}

TVSDK distribue des événements de qualité de service (QoS) pour informer votre application des événements susceptibles d’influencer le calcul des statistiques QoS, tels que la mise en mémoire tampon et la recherche d’événements.

L’exemple suivant illustre une progression type de ces événements :

```java
mediaPlayer.addEventListener(MediaPlayer.Event.QOS,  
  new MediaPlayer.QOSEventListener(){ 
    //For buffering activity 
    @Override 
    public void onBufferStart() 
    @Override 
    public void onBufferComplete() 
    // For seeking 
    @Override 
    public void onSeekStart() 
    @Override 
    public void onSeekComplete(long adjustedTime) 
    @Override 
    public void onLoadComplete (MediaPlayerItem mediaplayeritem) 
    @Override 
    public void onLoadInfo(LoadInfo loadInfo) 
    @Override 
    public void onOperationFailed(MediaPlayerNotification.Warning warning) 
});
```

## Événements DRM {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK distribue des événements DRM (Digital Rights Management, gestion des droits numériques) en réponse aux opérations liées à DRM, comme lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut mettre en oeuvre des actions en réponse à ces événements.

Pour être averti de tous les événements liés à DRM, écoutez `onDRMMetadata(DRMMetadataInfo drmMetadataInfo)`. TVSDK distribue des événements DRM supplémentaires par le biais de la fonction `DRMManager` classe .

L’exemple suivant illustre une progression type :

```
mediaPlayer.addEventListener(MediaPlayer.Event.DRM, 
 new MediaPlayer.DRMEventListener() { 
 @Override 
 public void onDRMMetadata(byte[] data, int length, long timestamp) {...} 
}); 
```

## Événements Loader {#section_5638F8EDACCE422A9425187484D39DCC}

Votre lecteur peut mettre en oeuvre des actions en fonction des événements suivants :

| Événement | Signification |
|---|---|
| `onLoadComplete (mediaPlayerItem playerItem)` | Chargement de la ressource multimédia terminé avec succès. |
| `onError` | Un problème s’est produit lors du chargement des ressources multimédia. |
