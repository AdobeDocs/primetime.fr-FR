---
description: Les événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles qu’une vidéo qui commence à lire, ou les actions qui se produisent implicitement, telles qu’une publicité qui se termine.
title: Écoute des événements du lecteur Primetime
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Aperçu {#implement-event-listeners-and-callbacks-overview}

Les gestionnaires de événements permettent à TVSDK de répondre aux événements. Lorsqu&#39;un événement se produit, le mécanisme de événement de TVSDK appelle votre gestionnaire de événements enregistré et transmet les informations du événement au gestionnaire.

L’exécution du Flash fournit un mécanisme de événement générique, que TVSDK utilise et définit également une série de événements personnalisés. Votre application doit mettre en oeuvre des écouteurs de événement pour les événements TVSDK qui affectent votre application.

Pour une liste complète des événements d’analyse vidéo, voir [Suivi de la lecture vidéo principale](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/c_vhl_track-core-vid-playback.html).

1. Déterminez quels événements votre application doit écouter.

   * **Événements** requis : Prêtez attention à tous les événements de lecture.

      >[!IMPORTANT]
      >
      >Le événement de lecture `MediaPlayerStatusChangeEvent.STATUS_CHANGE` indique l’état du lecteur, y compris les erreurs. L’un des états peut affecter l’étape suivante de votre lecteur.

   * **Autres événements** : Facultatif, selon votre application.

      Par exemple, si vous incorporez de la publicité dans votre lecture, écoutez tous les événements `AdBreakPlaybackEvent` et `AdPlaybackEvent`.

1. Mettez en oeuvre des écouteurs de événement pour chaque événement.

   TVSDK renvoie des valeurs de paramètre à vos rappels d’écouteur de événement. Ces valeurs fournissent des informations pertinentes sur le événement que vous pouvez utiliser dans vos écouteurs pour effectuer les actions appropriées.

   La classe `Event` liste toutes les interfaces de rappel. Chaque interface affiche les paramètres renvoyés pour cette interface.

   Par exemple :

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. Enregistrez vos écouteurs de rappel avec l&#39;objet `MediaPlayer` en utilisant `MediaPlayer.addEventListener`.

   `MediaPlayer` étend  `flash.events.IEventDispatcher`, qui fait partie des fichiers principaux du lecteur de Flash et inclut les fonctions  `addEventListener` et  `removeEventListener`les.

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```


