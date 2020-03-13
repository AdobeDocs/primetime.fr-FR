---
description: Les gestionnaires de  permettent à TVSDK de répondre aux  de.
seo-description: Les gestionnaires de  permettent à TVSDK de répondre aux  de.
seo-title: 'Mise en oeuvre des écouteurs et des rappels de '
title: 'Mise en oeuvre des écouteurs et des rappels de '
uuid: 6b7859a4-55f9-48b1-b1f1-7b79bc92610a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mise en oeuvre des écouteurs et des rappels de{#implement-event-listeners-and-callbacks}

Les gestionnaires de  permettent à TVSDK de répondre aux  de.

Lorsqu&#39;un se produit, le mécanisme de  de TVSDK appelle votre gestionnaire de  deréseau enregistré et transmet les informations de l&#39;au gestionnaire.

TVSDK définit les écouteurs comme des interfaces internes publiques dans l’ `MediaPlayer` interface.

Votre application doit mettre en oeuvre des écouteurs de  pour le TVSDK  qui affectent votre application.

Pour obtenir un complet du  pour les analyses vidéo, voir Suivi de la lecture vidéo principale.

1. Déterminez pour quel  votre application doit écouter.

   * **** obligatoire : Écoute tous les  de lecture.

      >[!IMPORTANT]
      >
      >Le de lecture `onStateChanged` fournit l’état du lecteur, y compris les erreurs. L’un des états peut affecter l’étape suivante du lecteur.

   * **Autre**: Facultatif, selon votre application.

      Par exemple, si vous incorporez de la publicité dans votre lecture, implémentez les rappels AdPlaybackEventListener.

1. Mettez en oeuvre des écouteurs  pour chaque  de.

   TVSDK renvoie des valeurs de paramètre à vos rappels d’écouteur de . Ces valeurs fournissent des informations pertinentes sur l’que vous pouvez utiliser dans vos écouteurs pour effectuer les actions appropriées.

   `MediaPlayer.EventListener`  toutes les interfaces de rappel. Chaque interface affiche le nom du rappel et les paramètres renvoyés pour chaque  de.

   Par exemple :

   ```
   MediaPlayer.PlaybackEventListener.onStateChanged( 
    MediaPlayer.PlayerState state, MediaPlayerNotification notification)
   ```

1. Enregistrez vos écouteurs de rappel avec l’ `MediaPlayer` objet à l’aide de `MediaPlayer.addEventListener`.

   ```
   mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, 
    new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onStateChanged( 
    MediaPlayer.PlayerState state, 
    MediaPlayerNotification notification) {...} 
   }
   ```

## Ordre du de lecture {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.

Les exemples suivants montrent l’ordre de certains  qui incluent des  de lecture.

* Lors du chargement réussi d’une ressource multimédia via `MediaPlayer.replaceCurrentResource`, l’ordre des  est le suivant :

1. `MediaPlayer.PlaybackEventListener.onStateChanged` with state `MediaPlayer.PlayerState.INITIALIZING`

1. `MediaPlayer.PlaybackEventListener.onStateChanged` with state `MediaPlayer.PlayerState.INITIALIZED`

>[!TIP]
>
>Chargez votre ressource multimédia sur le thread principal. Si vous chargez une ressource multimédia sur un thread d’arrière-plan, cette opération ou les opérations TVSDK suivantes, ou les deux, peuvent renvoyer une erreur (par exemple, `IllegalStateException`) et quitter.

* Lors de la préparation de la lecture `MediaPlayer.prepareToPlay`, l’ordre des  est le suivant :

1. `MediaPlayer.PlaybackEventListener.onStateChanged` with state `MediaPlayerStatus.PREPARING`

1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` si des publicités ont été insérées.
1. `MediaPlayer.PlaybackEventListener.onStateChanged` with state `MediaPlayerStatus.PREPARED`

* Pour les flux en direct/linéaires, pendant la lecture au fur et à mesure que la fenêtre de lecture avance et que des opportunités supplémentaires sont résolues, l’ordre des  est le suivant :

1. `MediaPlayer.PlaybackEventListener.onUpdated`
1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` si des publicités ont été insérées
1. `MediaPlayerItemEvent.ITEM_UPDATED`
1. `TimelineEvent.TIMELINE_UPDATED` si des publicités ont été insérées

L’exemple suivant illustre une progression type des  :

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

## Ordre des publicitaires {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Lorsque votre lecture comprend de la publicité, TVSDK envoie des /notifications dans des séquences généralement attendues. Votre lecteur peut mettre en oeuvre des actions basées sur des  dans la séquence prévue.

Lors de la lecture des publicités, l’ordre des  est le suivant :

* `AdPlaybackEventListener.onAdBreakStart`
* Les éléments suivants sont distribués pour chaque publicité de la coupure publicitaire :

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` (plusieurs fois pendant la lecture d’une publicité)
   * `AdPlaybackEventListener.onAdClick` (pour chaque clic)
   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdBreakComplete`

L’exemple suivant illustre une progression type du de lecture d’annonce :

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

Lors de la lecture des publicités, l’ordre des  est le suivant :

* `AdPlaybackEventListener.onAdBreakStart`
* Les éléments suivants sont distribués pour chaque publicité de la coupure publicitaire :

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` (plusieurs fois pendant la lecture d’une publicité)
   * `AdPlaybackEventListener.onAdClick` (pour chaque clic)
   * `AdPlaybackEventListener.onAdStart`

* `AdPlaybackEventListener.onAdBreakComplete`

L’exemple suivant illustre une progression type du de lecture d’annonce :

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

##  QoS {#section_9BFF3CD7AA1C4BD6960ACF6B9C0B25CC}

TVSDK distribue des  de qualité de service (QoS) pour avertir votre application de l’existence d’un susceptible d’influencer le calcul des statistiques de QoS, comme la mise en mémoire tampon et la recherche d’un .

L’exemple suivant illustre une progression type de ces  :

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

## DRM {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK distribue des  de gestion des droits numériques (DRM) en réponse aux opérations liées à la gestion des droits numériques, comme lorsque de nouvelles métadonnées DRM deviennent disponibles. Votre lecteur peut implémenter des actions en réponse à ces  de.

Pour être informé de tous les  de DRM, écoutez `onDRMMetadata(DRMMetadataInfo drmMetadataInfo)`. TVSDK distribue des DRM supplémentaires par l’intermédiaire de la `DRMManager` classe.

L’exemple suivant illustre une progression type :

```
mediaPlayer.addEventListener(MediaPlayer.Event.DRM, 
 new MediaPlayer.DRMEventListener() { 
 @Override 
 public void onDRMMetadata(byte[] data, int length, long timestamp) {...} 
}); 
```

## de chargement {#section_5638F8EDACCE422A9425187484D39DCC}

Votre lecteur peut implémenter des actions en fonction des  de suivants :

| Event | Signification |
|---|---|
| `onLoadComplete (mediaPlayerItem playerItem)` | Chargement de la ressource multimédia terminé. |
| `onError` | Un problème est survenu lors du chargement des ressources du média. |

