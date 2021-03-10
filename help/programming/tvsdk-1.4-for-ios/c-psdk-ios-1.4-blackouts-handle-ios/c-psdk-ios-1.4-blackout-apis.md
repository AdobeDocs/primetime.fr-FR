---
description: TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes d’électricité, notamment des méthodes, des métadonnées et des notifications.
title: Eléments de l’API Blackout
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Eléments de l’API Blackout{#blackout-api-elements}

TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes d’électricité, notamment des méthodes, des métadonnées et des notifications.

Vous pouvez utiliser les éléments suivants lors de la mise en oeuvre d’une solution de blackout dans votre lecteur.

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Enregistre la ressource actuellement chargée en tant que ressource en arrière-plan. Si `replaceCurrentItemWithPlayerItem` est appelé après cette méthode, TVSDK continue à télécharger le manifeste de l’élément d’arrière-plan jusqu’à ce que vous appeliez `unregisterCurrentBackgroundItem`, `stop` ou `reset` .

   * `unregisterCurrentBackgroundItem` Définit l&#39;élément d&#39;arrière-plan sur nil et arrête la récupération et l&#39;analyse du manifeste d&#39;arrière-plan.

* **PTMetadata.** PTBlackoutMetadata `PTMetadata` classe spécifique aux pannes d’électricité.

   Cela vous permet de définir des plages non recherchées (un tableau de `CMTimeRanges`) sur TVSDK. TVSDK vérifie ces plages chaque fois que l’utilisateur effectue une recherche. S’il est défini et que l’utilisateur effectue une recherche dans une plage non recherchée, TVSDK force le lecteur à la fin de la plage non recherchée.

* **DÉBUT ICI** **** NEXTPTAdMetadataActivez ou désactivez le prélecture sur un flux en direct en définissant  `enableLivePreroll` OUI ou NON. Si NON, TVSDK n’effectue pas d’appel de serveur publicitaire explicite pour les publicités preroll avant la lecture du contenu et ne lit donc pas la lecture preroll. Cela n&#39;a aucun impact sur les moyennes places. La valeur par défaut est YES.

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - Publié lorsque TVSDK détecte une balise abonnée dans le manifeste d’arrière-plan et qu’une nouvelle  `PTTimedMetadata` instance est préparée à partir de celui-ci. L&#39;objet de la notification est l&#39;instance `PTMediaPlayerItem` en cours de lecture. Vous pouvez récupérer l&#39;instance `PTTimedMetadata` à partir du dictionnaire `userInfo` de la notification à l&#39;aide de la clé `PTTimedMetadataKey`.

   * `PTBackgroundManifestErrorNotification` - Publié lorsque le lecteur multimédia ne parvient pas à charger le manifeste d’arrière-plan, c’est-à-dire que toutes les URL de diffusion en continu renvoient une erreur ou une réponse non valide. L&#39;objet de la notification est l&#39;instance `PTMediaPlayerItem` en cours de lecture.

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code : 204000
      * Type : Avertissement
      * Erreur lors du téléchargement du manifeste en arrière-plan.
   * `INVALID_SEEK_WARNING` Distribué lorsqu’une recherche est tentée dans une plage non recherchée ( `nonSeekableRanges` définie dans  `PTBlackoutMetadata`).


