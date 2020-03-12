---
description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
seo-description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
seo-title: Considérations et bonnes pratiques
title: Considérations et bonnes pratiques
uuid: 62a5d641-6f37-4e4d-bbc2-414bf3681d9c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Considérations et bonnes pratiques{#considerations-and-best-practices}

Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.

## Considérations {#section_tvsdk_considerations}

Tenez compte des informations suivantes lorsque vous utilisez TVSDK :

* Adobe Primetime ne fonctionne pas sur les émulateurs ou les simulateurs.

   Vous devez utiliser des périphériques réels pour les tests.
* La lecture n’est prise en charge que pour le contenu HLS (HTTP Live Streaming).
* Le contenu vidéo principal peut être multiplexé, où les flux vidéo et audio se trouvent dans le même rendu, ou non multiplexé, où les flux vidéo et audio se trouvent dans des rendus distincts.
* L’API TVSDK est implémentée dans ActionScript.
* La lecture vidéo nécessite le moteur vidéo Adobe (AVE). Cela a une incidence sur le mode et le moment d’accès aux ressources multimédia :

   * Le sous-titrage codé est pris en charge dans la mesure fournie par l’AVE.
   * Selon la précision de l’encodeur, la durée réelle du média codé peut différer de la durée enregistrée dans le manifeste de ressources de flux.

      Il n’existe aucun moyen fiable de resynchroniser entre la chronologie virtuelle idéale et la chronologie de la lecture réelle. Le suivi de la progression de la lecture du flux pour la gestion des publicités et les analyses vidéo doit utiliser le temps de lecture réel. Le comportement des  et de l’interface utilisateur peut donc ne pas suivre précisément le contenu multimédia et publicitaire.
   * Le nom de l’agent utilisateur entrant pour toutes les requêtes HTTP de TVSDK sur cette plateforme se voit attribuer le modèle de chaîne suivant :

      ```
      "Adobe Flash Player"
      ```

## Meilleures pratiques {#section_tvsdk_best_practices}

Voici les pratiques recommandées pour TVSDK :

* Utilisez HLS version 3.0 ou ultérieure pour le contenu  du.
* Pour TVSDK 1.4 pour DHLS, le chargement différé des publicités est activé par défaut.

   Pour le contenu sans preroll ou mid-roll, vous pouvez l’utiliser `AdvertisingMetadata.delayAdLoading` pour accélérer encore plus le chargement du contenu.

