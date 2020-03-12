---
description: TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de coupures d’Internet, notamment des méthodes, des métadonnées et des notifications.
seo-description: TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de coupures d’Internet, notamment des méthodes, des métadonnées et des notifications.
seo-title: Eléments de l’API Blackout
title: Eléments de l’API Blackout
uuid: ddc81558-4218-44d2-92df-15926c7c96b3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Eléments de l’API Blackout{#blackout-api-elements}

TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de coupures d’Internet, notamment des méthodes, des métadonnées et des notifications.

Vous pouvez utiliser les éléments suivants lors de l’implémentation d’une solution de blackout dans votre lecteur.

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Enregistre la ressource actuellement chargée comme ressource en arrière-plan. Si `replaceCurrentItemWithPlayerItem` est appelé après cette méthode, TVSDK continue à télécharger le manifeste de l’élément d’arrière-plan jusqu’à ce que vous appeliez `unregisterCurrentBackgroundItem` , `stop`ou `reset` .

   * `unregisterCurrentBackgroundItem` Définit l’élément d’arrière-plan sur nil et arrête la récupération et l’analyse du manifeste d’arrière-plan.

* **PTMetadata.PTBlackoutMetadata** Classe `PTMetadata` spécifique aux pannes d’électricité.

   Cela vous permet de définir des plages impossibles à rechercher (un tableau de `CMTimeRanges`) sur TVSDK. TVSDK vérifie ces plages chaque fois que l’utilisateur effectue une recherche. S’il est défini et que l’utilisateur effectue une recherche dans une plage non recherchée, TVSDK force le lecteur à la fin de la plage non recherchée.

* **ICI SUIVANT****PTAdMetadata** Activez ou désactivez le pré-roll sur un flux en direct en définissant `enableLivePreroll` OUI ou NON. Si NON, TVSDK n’effectue pas d’appel explicite du serveur d’annonces pour les publicités preroll avant la lecture du contenu et ne lit donc pas le pré-roll. Cela n&#39;a pas d&#39;impact sur le milieu des parcours. La valeur par défaut est YES.

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - Publié lorsque TVSDK détecte une balise abonnée dans le manifeste d’arrière-plan et qu’une nouvelle `PTTimedMetadata` instance est préparée à partir de celui-ci. L’objet de la notification est l’ `PTMediaPlayerItem` instance en cours de lecture. Vous pouvez récupérer l’ `PTTimedMetadata` instance à partir du `userInfo` dictionnaire de la notification à l’aide de la `PTTimedMetadataKey` clé.

   * `PTBackgroundManifestErrorNotification` - Publié lorsque le lecteur multimédia ne parvient pas à charger le manifeste d’arrière-plan, c’est-à-dire que toutes les URL de diffusion renvoient une erreur ou une réponse non valide. L’objet de la notification est l’ `PTMediaPlayerItem` instance en cours de lecture.

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code : 204000
      * Type : Avertissement
      * Erreur lors du téléchargement du manifeste en arrière-plan.
   * `INVALID_SEEK_WARNING` Distribué lorsqu’une recherche est tentée dans une plage non recherchée (dans `nonSeekableRanges` définie dans `PTBlackoutMetadata`).


