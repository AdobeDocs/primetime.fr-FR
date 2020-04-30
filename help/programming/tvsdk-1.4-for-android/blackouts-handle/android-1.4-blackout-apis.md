---
description: Vous pouvez gérer les coupures de courant dans les flux vidéo en direct et fournir un autre contenu pendant une coupure de courant.
seo-description: Vous pouvez gérer les coupures de courant dans les flux vidéo en direct et fournir un autre contenu pendant une coupure de courant.
seo-title: Eléments de l’API Blackout
title: Eléments de l’API Blackout
uuid: 263a8987-0c85-493a-9352-9605c877ba65
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Eléments de l’API Blackout{#blackout-api-elements}

Vous pouvez gérer les coupures de courant dans les flux vidéo en direct et fournir un autre contenu pendant une coupure de courant.

Lorsqu’une panne survient dans un flux en direct, votre lecteur utilise des gestionnaires de événement pour détecter la panne et fournir un autre contenu aux utilisateurs qui ne sont pas admissibles pour regarder le flux principal. Votre lecteur détecte le début et la fin de la période d’interruption, bascule la lecture du flux principal vers un flux alternatif et revient au flux principal à la fin de la période d’interruption.

Pour gérer les pannes de courant en direct :

1. Configurez votre application pour détecter les balises d’arrêt en vous abonnant aux balises d’arrêt dans un manifeste de diffusion en direct.

   TVSDK ne détecte pas de balises d’interruption de service par ses propres moyens ; vous devez vous abonner à des balises d&#39;arrêt pour recevoir une notification lorsque les balises sont rencontrées lors de l&#39;analyse du fichier manifeste.
1. Créez des écouteurs de événement pour les balises auxquelles votre lecteur est abonné (dans ce cas, les balises PLAYBACK et BLACKOUTS).

   Lorsqu’une balise se produit à laquelle votre lecteur s’est abonné (par exemple, une balise d’arrêt) dans le flux de premier plan (contenu principal) ou d’arrière-plan (contenu alternatif), TVSDK distribue une balise `TimedMetadataEvent` et crée une balise `TimedMetadataObject` pour le `TimedMetadataEvent`.

1. Mettez en oeuvre des gestionnaires pour les événements de métadonnées temporisés pour les flux de premier plan et d’arrière-plan.

   Dans ces gestionnaires, récupérez les heures de début et de fin de la période d’arrêt à partir des objets de événement de métadonnées minutés.
1. Créez des méthodes pour changer de contenu le début et la fin de la période d’interruption.

   Lorsque la période d’interruption début, basculez le contenu principal en arrière-plan et basculez le contenu alternatif pour en faire le flux principal. Continuez à récupérer et à analyser le manifeste d’origine en arrière-plan et continuez à rechercher la balise &quot;blackout end&quot;, de sorte que le lecteur puisse rejoindre le flux d’origine lorsque la coupure se termine.
1. Mettez à jour les plages impossibles à rechercher si la plage d’interruption se trouve dans le DVR du flux de lecture.

   Suivez et gérez le flux `TimedMetadata` en arrière-plan, en préparant et en mettant à jour des plages impossibles à rechercher.

TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes d’électricité, notamment des méthodes, des métadonnées et des notifications.

Vous pouvez utiliser les éléments suivants lors de la mise en oeuvre d’une solution de blackout dans votre lecteur.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Enregistre la ressource actuellement chargée en tant que ressource en arrière-plan. Si `replaceCurrentResource` est appelé après cette méthode, TVSDK continue à télécharger le manifeste de l’élément d’arrière-plan jusqu’à ce que vous appeliez `unregisterCurrentBackgroundItem`, `release`ou `reset`que vous appeliez.

   * `unregisterCurrentBackgroundItem` Définit l’élément d’arrière-plan sur null et arrête la récupération et l’analyse du manifeste d’arrière-plan.

* **BlackoutMetadata** -

   Une classe de métadonnées spécifique aux coupures de courant.

   Cela vous permet de définir des plages impossibles à rechercher (un tableau de `TimeRanges`) sur TVSDK. TVSDK vérifie ces plages chaque fois que l’utilisateur effectue une recherche. S’il est défini et que l’utilisateur effectue une recherche dans une plage non recherchée, TVSDK force le lecteur à la fin de la plage non recherchée.

* **DÉBUT ICI NEXT AdvertisingMetadata** Activez ou désactivez la pré-lecture sur un flux en direct en définissant `enableLivePreroll` la valeur true ou false. Si elle est définie sur false, TVSDK ne lance pas d’appel de serveur publicitaire explicite pour les publicités preroll avant la lecture du contenu et ne lit donc pas la lecture preroll. Cela n&#39;a aucun impact sur les moyennes places. La valeur par défaut est true.

* **MediaPlayer.BlackoutsEventListener**

   * `onTimedMetadataInBackgroundItem` - Distribué lorsque détecte une balise abonnée dans le manifeste d’arrière-plan et qu’une nouvelle `TimedMetadata` instance est préparée à partir de celui-ci. L’ `TimedMetadata` instance est distribuée en tant que paramètre.

   * `onBackgroundManifestFailed` - Distribué lorsque le lecteur multimédia ne parvient pas à charger le manifeste d’arrière-plan, c’est-à-dire que toutes les URL de diffusion en continu renvoient une erreur ou une réponse non valide.

* **Notifications**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code : 204000
      * Type : Avertissement
      * Erreur lors du téléchargement du manifeste en arrière-plan.