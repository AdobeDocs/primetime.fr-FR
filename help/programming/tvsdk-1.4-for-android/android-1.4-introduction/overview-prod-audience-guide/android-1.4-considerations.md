---
description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
seo-description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
seo-title: Considérations et bonnes pratiques
title: Considérations et bonnes pratiques
uuid: e698ae09-280b-4406-a9b8-4f468b7a6b9c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Considérations et bonnes pratiques{#considerations-and-best-practices}

Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.

## Considérations {#section_tvsdk_considerations}

Tenez compte des informations suivantes lorsque vous utilisez TVSDK :

* Adobe Primetime ne fonctionne pas actuellement sur les émulateurs Android.

   Vous devez utiliser des périphériques réels pour les tests.
* La lecture n’est prise en charge que pour le contenu HLS (HTTP Live Streaming).
* Le contenu vidéo principal peut être multiplexé, où les flux vidéo et audio se trouvent dans le même rendu, ou non multiplexé, où les flux vidéo et audio se trouvent dans des rendus distincts.
* L’API TVSDK est implémentée dans Java.
* Actuellement, vous devez exécuter la plupart des opérations de l’API TVSDK sur le thread de l’interface utilisateur, qui est le thread Android principal.

   Les opérations qui s’exécutent correctement sur le thread principal peuvent générer une erreur et se fermer lors de l’exécution sur un thread d’arrière-plan.
* La lecture vidéo nécessite le moteur vidéo Adobe (AVE). Cela a une incidence sur le mode et le moment d’accès aux ressources multimédia :

   * Le sous-titrage codé est pris en charge dans la mesure fournie par l’AVE.
   * Selon la précision de l’encodeur, la durée réelle du média codé peut différer de la durée enregistrée dans le manifeste de ressources de flux.

      Il n’existe aucun moyen fiable de resynchroniser entre la chronologie virtuelle idéale et la chronologie de la lecture réelle. Le suivi de la progression de la lecture du flux pour la gestion des publicités et les analyses vidéo doit utiliser le temps de lecture réel. Le comportement des  et de l’interface utilisateur peut donc ne pas suivre précisément le contenu multimédia et publicitaire.
   * Le nom de l’agent utilisateur entrant pour toutes les demandes de média issues du SDK TVSDK sur cette plate-forme se voit attribuer le modèle de chaîne suivant :

      ```
      "Adobe Primetime/ + 
      <varname>
      originalUserAgent
      </varname>" 
      ```

      Tous les appels liés aux publicités utilisent l’agent utilisateur par défaut Android ou l’agent utilisateur personnalisé si vous le définissez lors de la configuration des métadonnées d’insertion publicitaire.

## Meilleures pratiques {#section_tvsdk_best_practices}

Voici quelques recommandations pour TVSDK :

* Utilisez HLS version 3.0 ou ultérieure pour le contenu  du.
* Exécutez la plupart des opérations TVSDK dans le thread principal (IU), et non sur les threads en arrière-plan.
