---
description: TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes d’électricité, notamment des méthodes, des métadonnées et des notifications.
seo-description: TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes d’électricité, notamment des méthodes, des métadonnées et des notifications.
seo-title: Eléments de l’API Blackout
title: Eléments de l’API Blackout
uuid: 65e1668c-6a19-4910-83a2-46d364e94e5f
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Eléments de l’API Blackout{#blackout-api-elements}

TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes d’électricité, notamment des méthodes, des métadonnées et des notifications.

Vous pouvez utiliser les éléments suivants lors de la mise en oeuvre d’une solution de blackout dans votre lecteur.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Enregistre la ressource actuellement chargée en tant que ressource en arrière-plan. Si `replaceCurrentResource` est appelé après cette méthode, TVSDK continue à télécharger le manifeste de l’élément d’arrière-plan jusqu’à ce que vous appeliez `unregisterCurrentBackgroundItem`.

   * `unregisterCurrentBackgroundItem`  Efface la ressource d&#39;arrière-plan actuellement définie et arrête la récupération et l&#39;analyse du manifeste d&#39;arrière-plan.

* **Type de métadonnées** BlackoutMetadataType de métadonnées spécifique aux pannes d’électricité.

   Cela vous permet de définir des plages non recherchées (un attribut `TimeRange` supplémentaire appelé `nonseekableRange`) sur TVSDK. TVSDK vérifie ces plages (si la position de recherche souhaitée est comprise dans une `nonseekableRange`) chaque fois que l’utilisateur effectue une recherche. S’il est défini et que l’utilisateur effectue une recherche dans une plage non recherchée, TVSDK force le lecteur à l’heure de fin de `seekableRange`.

* **DÉBUT ICI** **** NEXTDefaultMetadataKeysActivez ou désactivez la pré-lecture sur un flux en direct en définissant  `ENABLE_LIVE_PREROLL` sur true ou false. Si elle est définie sur false, TVSDK ne lance pas d’appel de serveur publicitaire explicite pour les publicités preroll avant la lecture du contenu et ne lit donc pas la lecture preroll. Cela n&#39;a aucun impact sur les moyennes places. La valeur par défaut est true.

* **TimedMetadataEvent**

   * `TIMED_METADATA_IN_BACKGROUND_AVAILABLE` Sous-type de événement : distribué lorsque TVSDK détecte une balise abonnée dans le manifeste d’arrière-plan.

* **Notifications**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code : 204000
      * Type : Avertissement
      * Erreur lors du téléchargement du manifeste en arrière-plan.
   * `SeekEvent.SEEK_POSITION_ADJUSTED` Distribué lorsqu’une recherche est tentée dans une plage non recherchée.


