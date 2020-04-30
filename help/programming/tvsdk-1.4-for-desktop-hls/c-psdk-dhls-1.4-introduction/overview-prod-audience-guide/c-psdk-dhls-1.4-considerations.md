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

Rappelez-vous des informations suivantes lorsque vous utilisez TVSDK :

* Adobe Primetime ne fonctionne pas sur les émulateurs ou les simulateurs.

   Vous devez utiliser des périphériques réels pour les tests.
* La lecture n’est prise en charge que pour le contenu HLS (HTTP Live Streaming).
* Le contenu vidéo principal peut être multiplexé, où les flux vidéo et audio se trouvent dans le même rendu, ou non multiplexé, où les flux vidéo et audio se trouvent dans des rendus distincts.
* L’API TVSDK est implémentée dans ActionScript.
* La lecture vidéo nécessite Adobe Video Engine (AVE). Cela a une incidence sur le mode et le moment d’accès aux ressources multimédia :

   * Le sous-titrage est pris en charge dans la mesure prévue par l&#39;AVE.
   * Selon la précision de l’encodeur, la durée réelle du support codé peut différer des durées enregistrées dans le manifeste de ressources de diffusion en continu.

      Il n&#39;existe aucun moyen fiable de resynchroniser entre la chronologie virtuelle idéale et la chronologie de la lecture réelle. Le suivi de la progression de la lecture du flux pour la gestion des publicités et les analyses vidéo doit utiliser le temps de lecture réel. Par conséquent, le comportement des rapports et de l’interface utilisateur peut ne pas suivre précisément le contenu multimédia et publicitaire.
   * Le nom de l’agent utilisateur entrant pour toutes les requêtes HTTP de TVSDK sur cette plate-forme se voit attribuer le modèle de chaîne suivant :

      ```
      "Adobe Flash Player"
      ```

## Meilleures pratiques {#section_tvsdk_best_practices}

Voici les pratiques recommandées pour TVSDK :

* Utilisez HLS version 3.0 ou ultérieure pour le contenu du programme.
* Pour TVSDK 1.4 pour DHLS, le chargement différé des publicités est activé par défaut.

   Pour le contenu sans preroll ou mid-roll, vous pouvez l’utiliser `AdvertisingMetadata.delayAdLoading` pour accélérer encore plus le chargement du contenu.

