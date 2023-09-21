---
description: TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes de courant, notamment des méthodes, des métadonnées et des notifications.
title: Éléments de l’API de blackout
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Éléments de l’API de blackout{#blackout-api-elements}

TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes de courant, notamment des méthodes, des métadonnées et des notifications.

Vous pouvez utiliser les éléments suivants lors de la mise en oeuvre d’une solution de blackout dans votre lecteur.

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Enregistre la ressource actuellement chargée comme ressource d’arrière-plan. If `replaceCurrentItemWithPlayerItem` est appelé après cette méthode, TVSDK continue de télécharger le manifeste de l’élément en arrière-plan jusqu’à ce que vous appeliez `unregisterCurrentBackgroundItem` , `stop`, ou `reset` .

   * `unregisterCurrentBackgroundItem` Définit l’élément d’arrière-plan sur nil et arrête la récupération et l’analyse du manifeste d’arrière-plan.

* **PTMetadata.PTBlackoutMetadata** A `PTMetadata` qui est spécifique aux blackout.

  Cela vous permet de définir des plages impossibles à rechercher (un tableau de `CMTimeRanges`) sur TVSDK. TVSDK recherche ces plages chaque fois que l’utilisateur effectue une recherche. S’il est défini et que l’utilisateur effectue une recherche dans une plage non consultable, TVSDK force la visionneuse à la fin de la plage non consultable.

* **COMMENCER ICI SUIVANT** **PTAdMetadata** Activation ou désactivation du preroll sur un flux en direct en définissant `enableLivePreroll` à OUI ou NON. Si NON, TVSDK n’effectue pas d’appel de serveur de publicités explicite pour les publicités preroll avant la lecture du contenu et ne lit donc pas la lecture preroll. Cela n&#39;a aucun impact sur les moyennes. La valeur par défaut est YES.

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - Publié lorsque TVSDK détecte une balise abonnée dans le manifeste d’arrière-plan et un nouveau `PTTimedMetadata` est préparée à partir de celle-ci. L’objet de la notification est `PTMediaPlayerItem` instance en cours de lecture. Vous pouvez récupérer la variable `PTTimedMetadata` à partir de l’instance de notification `userInfo` dictionnaire utilisant la variable `PTTimedMetadataKey` clé.

   * `PTBackgroundManifestErrorNotification` - Publiées lorsque le lecteur multimédia ne parvient pas à charger le manifeste en arrière-plan, c’est-à-dire que toutes les URL de diffusion renvoient une erreur ou une réponse non valide. L’objet de la notification est `PTMediaPlayerItem` instance en cours de lecture.

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code : 204000
      * Type : Avertissement
      * Erreur lors du téléchargement du manifeste en arrière-plan.

   * `INVALID_SEEK_WARNING` Distribué lorsqu’une recherche est tentée dans une plage non visible (dans `nonSeekableRanges` set in `PTBlackoutMetadata`).
