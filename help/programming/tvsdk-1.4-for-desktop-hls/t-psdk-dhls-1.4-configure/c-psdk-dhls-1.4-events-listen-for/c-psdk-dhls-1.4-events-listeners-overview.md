---
description: Les événements de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, la fin des actions que vous avez demandées, telles que le démarrage de la lecture d’une vidéo ou les actions qui se produisent implicitement, telles qu’une fin de publicité.
title: Écoute des événements du lecteur Primetime
exl-id: 3a740245-a9e1-4e36-8761-f9f4b4e85b93
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Présentation {#implement-event-listeners-and-callbacks-overview}

Les gestionnaires d’événements permettent à TVSDK de répondre aux événements. Lorsqu’un événement se produit, le mécanisme d’événement de TVSDK appelle votre gestionnaire d’événements enregistré et transmet les informations d’événement au gestionnaire.

Flash Runtime fournit un mécanisme d’événements générique, que TVSDK utilise et définit également une série d’événements personnalisés. Votre application doit mettre en oeuvre des écouteurs d’événements pour les événements TVSDK qui affectent votre application.

1. Déterminez les événements que votre application doit écouter.

   * **Événements** requis : Prêtez attention à tous les événements de lecture.

      >[!IMPORTANT]
      >
      >L’événement de lecture `MediaPlayerStatusChangeEvent.STATUS_CHANGE` fournit l’état du lecteur, y compris les erreurs. L’un des états peut affecter l’étape suivante de votre lecteur.

   * **Autres événements** : Facultatif, selon votre application.

      Par exemple, si vous incorporez de la publicité dans votre lecture, écoutez tous les événements `AdBreakPlaybackEvent` et `AdPlaybackEvent`.

1. Mettez en oeuvre des écouteurs d’événement pour chaque événement.

   TVSDK renvoie des valeurs de paramètre à vos rappels d’écouteurs d’événements. Ces valeurs fournissent des informations pertinentes sur l’événement que vous pouvez utiliser dans vos écouteurs pour effectuer les actions appropriées.

   La classe `Event` répertorie toutes les interfaces de rappel. Chaque interface affiche les paramètres renvoyés pour cette interface.

   Par exemple :

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. Enregistrez vos écouteurs de rappel avec l’objet `MediaPlayer` à l’aide de `MediaPlayer.addEventListener`.

   `MediaPlayer` étend  `flash.events.IEventDispatcher`, qui fait partie des fichiers principaux du lecteur Flash et inclut les fonctions  `addEventListener` et  `removeEventListener`.

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```
