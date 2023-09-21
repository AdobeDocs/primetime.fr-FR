---
description: Vous pouvez gérer les pannes de courant dans les diffusions vidéo en direct et fournir un contenu alternatif lors d’une panne.
title: Éléments de l’API de blackout
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Éléments de l’API de blackout{#blackout-api-elements}

Vous pouvez gérer les pannes de courant dans les diffusions vidéo en direct et fournir un contenu alternatif lors d’une panne.

Lorsqu’un blackout se produit dans un flux en direct, votre lecteur utilise des gestionnaires d’événements pour détecter le blackout et fournir un contenu alternatif à ces utilisateurs qui ne sont pas éligibles pour regarder le flux principal. Votre lecteur détecte le début et la fin de la période d’interruption, bascule la lecture de la diffusion principale vers une diffusion alternative et revient à la diffusion principale lorsque la période d’interruption se termine.

Pour gérer les pannes de courant dans les flux en direct :

1. Configurez votre application pour détecter les balises de blackout en vous abonnant aux balises de blackout dans un manifeste de diffusion en direct.

   TVSDK ne détecte pas les balises de blackout par lui-même ; vous devez vous abonner aux balises de blackout pour recevoir une notification lorsque les balises sont rencontrées lors de l’analyse du fichier manifeste.
1. Créez des écouteurs d’événement pour les balises auxquelles votre lecteur est abonné (dans ce cas, les balises LECTURE et SAUF) .

   Lorsqu’une balise se produit à laquelle votre lecteur s’est abonné (par exemple, une balise d’interruption) dans les manifestes de diffusion de premier plan (contenu principal) ou en arrière-plan (contenu alternatif), TVSDK envoie une `TimedMetadataEvent` et crée une `TimedMetadataObject` pour le `TimedMetadataEvent`.

1. Mettez en oeuvre des gestionnaires pour les événements de métadonnées minutés pour les flux de premier plan et d’arrière-plan.

   Dans ces gestionnaires, obtenez les heures de début et de fin de la période d’interruption à partir des objets d’événement de métadonnées minutés.
1. Créez des méthodes pour changer de contenu au début et à la fin de la période de blackout.

   Au début de la période d’interruption, basculez le contenu principal en arrière-plan et changez le contenu alternatif pour devenir la diffusion principale. Continuez à récupérer et à analyser le manifeste d’origine en arrière-plan et à rechercher la balise &quot;blackout end&quot;, de sorte que le lecteur puisse rejoindre le flux d’origine à la fin du blackout.
1. Mettez à jour les plages non consultables si la plage d’interruption se trouve dans le répertoire de stockage global de documents (DVR) de la diffusion.

   Suivez et gérez les `TimedMetadata` dans le flux d’arrière-plan, en préparant et en mettant à jour les plages impossibles à rechercher.

TVSDK fournit des éléments d’API utiles lors de la mise en oeuvre de pannes de courant, notamment des méthodes, des métadonnées et des notifications.

Vous pouvez utiliser les éléments suivants lors de la mise en oeuvre d’une solution de blackout dans votre lecteur.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Enregistre la ressource actuellement chargée comme ressource d’arrière-plan. If `replaceCurrentResource` est appelé après cette méthode, TVSDK continue de télécharger le manifeste de l’élément en arrière-plan jusqu’à ce que vous appeliez `unregisterCurrentBackgroundItem`, `release`, ou `reset`.

   * `unregisterCurrentBackgroundItem` Définit l’élément d’arrière-plan sur null et arrête la récupération et l’analyse du manifeste d’arrière-plan.

* **BlackoutMetadata** -

  Une classe de métadonnées spécifique aux blackout.

  Cela vous permet de définir des plages impossibles à rechercher (un tableau de `TimeRanges`) sur TVSDK. TVSDK recherche ces plages chaque fois que l’utilisateur effectue une recherche. S’il est défini et que l’utilisateur effectue une recherche dans une plage non consultable, TVSDK force la visionneuse à la fin de la plage non consultable.

* **COMMENCER ICI NEXT AdvertisingMetadata** Activation ou désactivation de preroll sur un flux en direct en définissant `enableLivePreroll` sur true ou false. Si la valeur est false, TVSDK n’effectue pas d’appel de serveur de publicités explicite pour les publicités preroll avant la lecture du contenu et ne lit donc pas la publicité preroll. Cela n&#39;a aucun impact sur les moyennes. La valeur par défaut est true.

* **MediaPlayer.BlackoutsEventListener**

   * `onTimedMetadataInBackgroundItem` - Dispatché lorsqu’il détecte une balise abonnée dans le manifeste d’arrière-plan et une nouvelle balise `TimedMetadata` est préparée à partir de celle-ci. La variable `TimedMetadata` est diffusée en tant que paramètre.

   * `onBackgroundManifestFailed` - Distribué lorsque le lecteur multimédia ne parvient pas à charger complètement le manifeste en arrière-plan, c’est-à-dire que toutes les URL de diffusion renvoient une erreur ou une réponse non valide.

* **Notifications**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code : 204000
      * Type : Avertissement
      * Erreur lors du téléchargement du manifeste en arrière-plan.
