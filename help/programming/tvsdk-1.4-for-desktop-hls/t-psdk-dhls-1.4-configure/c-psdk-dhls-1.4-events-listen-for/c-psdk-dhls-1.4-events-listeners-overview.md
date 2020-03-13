---
description: Les  de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, l’achèvement des actions que vous avez demandées, comme le démarrage de la lecture d’une vidéo, ou les actions qui se produisent implicitement, comme l’achèvement d’une publicité.
seo-description: Les  de TVSDK indiquent l’état du lecteur, les erreurs qui se produisent, l’achèvement des actions que vous avez demandées, comme le démarrage de la lecture d’une vidéo, ou les actions qui se produisent implicitement, comme l’achèvement d’une publicité.
seo-title: 'Écoute du de Primetime Player '
title: 'Écoute du de Primetime Player '
uuid: e72782bf-9d26-4285-85e4-fd4d803c1bbe
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Présentation {#implement-event-listeners-and-callbacks-overview}

Les gestionnaires de  permettent à TVSDK de répondre aux  de. Lorsqu&#39;un se produit, le mécanisme de  de TVSDK appelle votre gestionnaire de  deréseau enregistré et transmet les informations de l&#39;au gestionnaire.

Flash Runtime fournit un mécanisme de  générique, que TVSDK utilise et définit également une série de  personnalisées. Votre application doit mettre en oeuvre des écouteurs de  pour le TVSDK  qui affectent votre application.

Pour obtenir un  complet du  pour les analyses vidéo, reportez-vous à la section [Suivi de la lecture](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/c_vhl_track-core-vid-playback.html)vidéo de base.

1. Déterminez pour quel  votre application doit écouter.

   * **** obligatoire : Écoute tous les  de lecture.

      >[!IMPORTANT]
      >
      >Le  de lecture `MediaPlayerStatusChangeEvent.STATUS_CHANGE` fournit l’état du lecteur, y compris les erreurs. N’importe quel état peut affecter l’étape suivante de votre lecteur.

   * **Autre**: Facultatif, selon votre application.

      Si, par exemple, vous incorporez de la publicité dans votre lecture, écoutez tous les `AdBreakPlaybackEvent` et les `AdPlaybackEvent` .

1. Mettez en oeuvre des écouteurs  pour chaque  de.

   TVSDK renvoie des valeurs de paramètre à vos rappels d’écouteur de . Ces valeurs fournissent des informations pertinentes sur l’que vous pouvez utiliser dans vos écouteurs pour effectuer les actions appropriées.

   La `Event` classe toutes les interfaces de rappel. Chaque interface affiche les paramètres renvoyés pour cette interface.

   Par exemple :

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. Enregistrez vos écouteurs de rappel avec l’ `MediaPlayer` objet à l’aide de `MediaPlayer.addEventListener`.

   `MediaPlayer` étend `flash.events.IEventDispatcher`, qui fait partie des fichiers principaux du lecteur Flash et inclut les fonctions `addEventListener` et `removeEventListener`.

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```


