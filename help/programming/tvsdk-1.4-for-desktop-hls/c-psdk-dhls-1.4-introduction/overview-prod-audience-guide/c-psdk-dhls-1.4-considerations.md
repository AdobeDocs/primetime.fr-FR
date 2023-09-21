---
description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
title: Considérations et bonnes pratiques
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Considérations et bonnes pratiques{#considerations-and-best-practices}

Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.

## Considérations {#section_tvsdk_considerations}

Gardez à l’esprit les informations suivantes lorsque vous utilisez TVSDK :

* Adobe Primetime ne fonctionne pas sur les émulateurs ou les simulateurs.

  Vous devez utiliser des appareils réels pour les tests.
* La lecture est prise en charge uniquement pour le contenu HTTP Live Streaming (HLS).
* Le contenu vidéo principal peut être multiplexé, où les diffusions vidéo et audio se trouvent dans le même rendu, ou non multiplexé, où les diffusions vidéo et audio se trouvent dans des rendus distincts.
* L’API TVSDK est implémentée dans ActionScript.
* La lecture vidéo nécessite le moteur vidéo d’Adobe (AVE). Cela a une incidence sur la manière et le moment où les ressources multimédia peuvent être consultées :

   * Le sous-titrage codé est pris en charge dans la mesure fournie par l’AVE.
   * Selon la précision de l’encodeur, la durée réelle du média codé peut différer des durées enregistrées dans le manifeste de ressource de flux.

     Il n’existe aucun moyen fiable de resynchroniser entre la chronologie virtuelle idéale et la chronologie réelle de lecture. Le suivi de la progression de la lecture de la diffusion pour la gestion des publicités et les analyses vidéo doit utiliser le temps de lecture réel. Par conséquent, le comportement de la création de rapports et de l’interface utilisateur peut ne pas suivre précisément le contenu multimédia et publicitaire.
   * Le modèle de chaîne suivant est attribué au nom de l’agent utilisateur entrant pour toutes les requêtes HTTP issues de TVSDK sur cette plate-forme :

     ```
     "Adobe Flash Player"
     ```

## Bonnes pratiques {#section_tvsdk_best_practices}

Voici les pratiques recommandées pour TVSDK :

* Utilisez HLS version 3.0 ou ultérieure pour le contenu du programme.
* Pour TVSDK 1.4 pour DHLS, le chargement différé des publicités est activé par défaut.

  Pour le contenu sans preroll ou mid-roll, vous pouvez utiliser `AdvertisingMetadata.delayAdLoading` pour accélérer encore plus le chargement du contenu.
