---
description: TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes de courant, notamment des méthodes, des métadonnées et des notifications.
title: Éléments de l’API de blackout
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Éléments de l’API de blackout{#blackout-api-elements}

TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes de courant, notamment des méthodes, des métadonnées et des notifications.

Vous pouvez utiliser les éléments suivants lors de la mise en oeuvre d’une solution de blackout dans votre lecteur.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Enregistre la ressource actuellement chargée comme ressource d’arrière-plan. If `replaceCurrentResource` est appelé après cette méthode, TVSDK continue de télécharger le manifeste de l’élément en arrière-plan jusqu’à ce que vous appeliez `unregisterCurrentBackgroundItem`.

   * `unregisterCurrentBackgroundItem`  Efface la ressource d’arrière-plan actuellement définie et arrête la récupération et l’analyse du manifeste d’arrière-plan.

* **BlackoutMetadata** Type de métadonnées spécifique aux blackout.

  Cela vous permet de définir des plages impossibles à rechercher (une `TimeRange` attribut appelé `nonseekableRange`) sur TVSDK. TVSDK vérifie ces plages (si la position de recherche souhaitée est comprise dans une `nonseekableRange`) chaque fois que l’utilisateur effectue une recherche. S’il est défini et que l’utilisateur effectue une recherche dans une plage non consultable, TVSDK force la visionneuse à l’heure de fin de la variable `seekableRange`.

* **COMMENCER ICI SUIVANT** **DefaultMetadataKeys** Activation ou désactivation de preroll sur un flux en direct en définissant `ENABLE_LIVE_PREROLL` sur true ou false. Si la valeur est false, TVSDK n’effectue pas d’appel de serveur de publicités explicite pour les publicités preroll avant la lecture du contenu et ne lit donc pas la publicité preroll. Cela n&#39;a aucun impact sur les moyennes. La valeur par défaut est true.

* **TimedMetadataEvent**

   * `TIMED_METADATA_IN_BACKGROUND_AVAILABLE` sous-type d’événement : distribué lorsque TVSDK détecte une balise abonnée dans le manifeste d’arrière-plan.

* **Notifications**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code : 204000
      * Type : Avertissement
      * Erreur lors du téléchargement du manifeste en arrière-plan.

   * `SeekEvent.SEEK_POSITION_ADJUSTED` Distribué lorsqu’une recherche est tentée dans une plage non visible.
