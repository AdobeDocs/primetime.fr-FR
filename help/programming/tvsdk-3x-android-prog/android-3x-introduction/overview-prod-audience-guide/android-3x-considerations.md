---
description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
seo-description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
seo-title: Considérations et bonnes pratiques
title: Considérations et bonnes pratiques
uuid: a65c9739-ed83-4519-8ae5-7ba4c8f1ca49
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Considérations et bonnes pratiques {#considerations-and-best-practices}

Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.

## Considérations {#section_tvsdk_considerations}

Tenez compte des informations suivantes lorsque vous utilisez TVSDK :

* L’API TVSDK est implémentée dans Java.
* Adobe Primetime ne fonctionne pas actuellement sur les émulateurs Android.

   Vous devez utiliser des périphériques réels pour les tests.
* La lecture n’est prise en charge que pour le contenu HLS (HTTP Live Streaming).
* Le contenu vidéo principal peut être multiplexé (flux vidéo et audio dans le même rendu) ou non multiplexé (flux vidéo et audio dans des rendus distincts).
* Actuellement, vous devez exécuter la plupart des opérations de l’API TVSDK sur le thread de l’interface utilisateur, qui est le thread Android principal.

   Les opérations qui s’exécutent correctement sur le thread principal peuvent générer une erreur et se fermer lors de l’exécution sur un thread d’arrière-plan.
* La lecture vidéo nécessite le moteur vidéo Adobe (AVE). Cela a une incidence sur le mode et le moment d’accès aux ressources multimédia :

   * Le sous-titrage codé est pris en charge dans la mesure fournie par l’AVE.
   * Selon la précision de l’encodeur, la durée réelle du média codé peut différer de la durée enregistrée dans le manifeste de ressources de flux.

      Il n’existe aucun moyen fiable de resynchroniser entre la chronologie virtuelle idéale et la chronologie de la lecture réelle. Le suivi de la progression de la lecture du flux pour la gestion des publicités et les analyses vidéo doit utiliser le temps de lecture réel. Le comportement des  et de l’interface utilisateur peut donc ne pas suivre précisément le contenu multimédia et publicitaire.
   * Le nom de l’agent utilisateur entrant pour toutes les demandes de média issues du SDK TVSDK sur cette plate-forme se voit attribuer le modèle de chaîne suivant :

      ```
      "Adobe Primetime/" + originalUserAgent
      ```

      Tous les appels liés aux publicités utilisent l’agent utilisateur par défaut Android ou l’agent utilisateur personnalisé si vous le définissez lors de la configuration des métadonnées d’insertion publicitaire.

## Meilleures pratiques {#section_tvsdk_best_practices}

Voici quelques recommandations pour TVSDK :

* Utilisez HLS version 3.0 ou ultérieure pour le contenu  du.
* Exécutez la plupart des opérations TVSDK sur le thread principal (interface utilisateur), et non sur les threads en arrière-plan.
* Pour TVSDK 3.0 pour Android, la résolution différée des publicités est activée par défaut.

Pour le contenu sans preroll ou mid-roll, vous pouvez utiliser `AdvertisingMetadata.setPreroll(false)` pour accélérer le chargement du contenu.