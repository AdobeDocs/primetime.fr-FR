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

Rappelez-vous des informations suivantes lorsque vous utilisez TVSDK :

* Adobe Primetime ne fonctionne pas actuellement sur les émulateurs Android.

   Vous devez utiliser des périphériques réels pour les tests.
* La lecture n’est prise en charge que pour le contenu HLS (HTTP Live Streaming).
* Le contenu vidéo principal peut être multiplexé, où les flux vidéo et audio se trouvent dans le même rendu, ou non multiplexé, où les flux vidéo et audio se trouvent dans des rendus distincts.
* L’API TVSDK est implémentée dans Java.
* Actuellement, vous devez exécuter la plupart des opérations de l’API TVSDK sur le thread d’interface utilisateur, qui est le thread Android principal.

   Les opérations qui s&#39;exécutent correctement sur le thread principal peuvent générer une erreur et se fermer lors de l&#39;exécution sur un thread en arrière-plan.
* La lecture vidéo nécessite Adobe Video Engine (AVE). Cela a une incidence sur le mode et le moment d’accès aux ressources multimédia :

   * Le sous-titrage est pris en charge dans la mesure prévue par l&#39;AVE.
   * Selon la précision de l’encodeur, la durée réelle du support codé peut différer des durées enregistrées dans le manifeste de ressources de diffusion en continu.

      Il n’existe aucun moyen fiable de resynchroniser entre la chronologie virtuelle idéale et la chronologie de la lecture réelle. Le suivi de la progression de la lecture du flux pour la gestion des publicités et les analyses vidéo doit utiliser le temps de lecture réel. Par conséquent, le comportement des rapports et de l’interface utilisateur peut ne pas suivre précisément le contenu multimédia et publicitaire.
   * Le nom de l’agent utilisateur entrant pour toutes les requêtes multimédias de TVSDK sur cette plate-forme se voit attribuer le modèle de chaîne suivant :

      ```
      "Adobe Primetime/ + 
      <varname>
      originalUserAgent
      </varname>" 
      ```

      Tous les appels liés à la publicité utilisent l’agent utilisateur par défaut d’Android ou l’agent utilisateur personnalisé si vous le définissez lors de la configuration des métadonnées d’insertion publicitaire.

## Meilleures pratiques {#section_tvsdk_best_practices}

Voici les pratiques recommandées pour TVSDK :

* Utilisez HLS version 3.0 ou ultérieure pour le contenu du programme.
* Exécutez la plupart des opérations TVSDK dans le thread principal (IU), et non sur les threads en arrière-plan.
