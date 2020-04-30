---
description: Les Événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.
seo-description: Les Événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.
seo-title: Écoute des événements du lecteur Primetime
title: Écoute des événements du lecteur Primetime
uuid: e72782bf-9d26-4285-85e4-fd4d803c1bbe
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Présentation {#implement-event-listeners-and-callbacks-overview}

Les gestionnaires de Événements permettent à TVSDK de répondre aux événements. Lorsqu&#39;un événement se produit, le mécanisme de événement de TVSDK appelle votre gestionnaire de événements enregistré et transmet les informations du événement au gestionnaire.

Flash Runtime fournit un mécanisme de événements génériques, que TVSDK utilise et définit également une série de événements personnalisés. Votre application doit mettre en oeuvre des écouteurs de événement pour les événements TVSDK qui affectent votre application.

Pour obtenir une liste complète des événements d’analyse vidéo, reportez-vous à la section [Suivi de la lecture](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/c_vhl_track-core-vid-playback.html)vidéo de base.

1. Déterminez quels événements votre application doit écouter.

   * **événements** requis : Prêtez attention à tous les événements de lecture.

      >[!IMPORTANT]
      >
      >Le événement de lecture `MediaPlayerStatusChangeEvent.STATUS_CHANGE` indique l’état du lecteur, y compris les erreurs. L’un des états peut affecter l’étape suivante de votre lecteur.

   * **Autres événements**: Facultatif, selon votre application.

      Par exemple, si vous incorporez de la publicité dans votre lecture, écoutez tous les `AdBreakPlaybackEvent` `AdPlaybackEvent` événements et tous les autres.

1. Mettez en oeuvre des écouteurs de événement pour chaque événement.

   TVSDK renvoie des valeurs de paramètre à vos rappels d’écouteur de événement. Ces valeurs fournissent des informations pertinentes sur le événement que vous pouvez utiliser dans vos écouteurs pour effectuer les actions appropriées.

   La `Event` classe liste toutes les interfaces de rappel. Chaque interface affiche les paramètres renvoyés pour cette interface.

   Par exemple :

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. Enregistrez vos écouteurs de rappel avec l’ `MediaPlayer` objet à l’aide de `MediaPlayer.addEventListener`.

   `MediaPlayer` étend `flash.events.IEventDispatcher`, qui fait partie des fichiers de base du lecteur Flash et inclut les fonctions `addEventListener` et `removeEventListener`.

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```


