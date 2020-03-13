---
description: TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de coupures d’Internet, notamment des méthodes, des métadonnées et des notifications.
seo-description: TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de coupures d’Internet, notamment des méthodes, des métadonnées et des notifications.
seo-title: Eléments de l’API Blackout
title: Eléments de l’API Blackout
uuid: 65e1668c-6a19-4910-83a2-46d364e94e5f
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Eléments de l’API Blackout{#blackout-api-elements}

TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de coupures d’Internet, notamment des méthodes, des métadonnées et des notifications.

Vous pouvez utiliser les éléments suivants lors de l’implémentation d’une solution de blackout dans votre lecteur.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Enregistre la ressource actuellement chargée comme ressource en arrière-plan. Si `replaceCurrentResource` est appelé après cette méthode, TVSDK continue à télécharger le manifeste de l’élément d’arrière-plan jusqu’à ce que vous appeliez `unregisterCurrentBackgroundItem`.

   * `unregisterCurrentBackgroundItem`  Efface la ressource d’arrière-plan actuellement définie et arrête de récupérer et d’analyser le manifeste d’arrière-plan.

* **Métadonnées** de coupure de courant Type de métadonnées spécifique aux coupures de courant.

   Cela vous permet de définir des plages impossibles à rechercher (un attribut supplémentaire appelé `TimeRange` `nonseekableRange`) sur TVSDK. TVSDK vérifie ces plages (si la position de recherche souhaitée est comprise dans une `nonseekableRange`) chaque fois que l’utilisateur effectue une recherche. S’il est défini et que l’utilisateur effectue une recherche dans une plage non recherchée, TVSDK force le lecteur à l’heure de fin de la `seekableRange`.

* **ICI SUIVANT** **DefaultMetadataKeys** Activez ou désactivez la fonction preroll sur un flux en direct en définissant `ENABLE_LIVE_PREROLL` sur true ou false. Si la valeur est false, TVSDK n’effectue pas d’appel explicite du serveur d’annonces pour les publicités preroll avant la lecture du contenu et ne lit donc pas la lecture preroll. Cela n&#39;a pas d&#39;impact sur le milieu des parcours. La valeur par défaut est true.

* **TimedMetadataEvent**

   * `TIMED_METADATA_IN_BACKGROUND_AVAILABLE` Sous-type de  - Distribué lorsque TVSDK détecte une balise abonnée dans le manifeste d’arrière-plan.

* **Notifications**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code : 204000
      * Type : Avertissement
      * Erreur lors du téléchargement du manifeste en arrière-plan.
   * `SeekEvent.SEEK_POSITION_ADJUSTED` Distribué lorsqu’une recherche est tentée dans une plage non recherchée.


