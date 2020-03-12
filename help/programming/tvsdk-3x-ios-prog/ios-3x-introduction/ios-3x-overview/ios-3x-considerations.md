---
description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
seo-description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
seo-title: Considérations et bonnes pratiques
title: Considérations et bonnes pratiques
uuid: a65c9739-ed83-4519-8ae5-7ba4c8f1ca49
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Considérations et bonnes pratiques {#considerations-and-best-practices}

Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.

## Considérations {#section_tvsdk_considerations}

Tenez compte des informations suivantes lorsque vous utilisez TVSDK :

* Adobe Primetime ne fonctionne pas sur les simulateurs iOS.

   Vous devez utiliser des périphériques réels pour les tests.

* La lecture n’est prise en charge que pour le contenu HLS (HTTP Live Streaming).

* Le contenu vidéo principal peut être multiplexé, où les flux vidéo et audio se trouvent dans le même rendu, ou non multiplexé, où les flux vidéo et audio se trouvent dans des rendus distincts.

* L’API TVSDK est implémentée dans Objective-C.

* La lecture vidéo requiert la structure native d’Apple AV Foundation. Cela a une incidence sur la manière et le moment d’accéder aux ressources multimédia, notamment aux sous-titres et aux calendriers fermés :

   * Les réglages de la chronologie ne peuvent pas être modifiés après la configuration initiale.

      Par exemple, une publicité ne peut pas être supprimée du plan de montage chronologique une fois qu’elle a été lue. Si l’utilisateur effectue une nouvelle recherche dans la présentation, la même publicité est relue même si la stratégie consistait à supprimer la publicité.

   * Selon la précision de l’encodeur, la durée réelle du média codé peut différer de la durée enregistrée dans le manifeste de ressources de flux.

      Il n’existe aucun moyen fiable de resynchroniser entre la chronologie virtuelle idéale et la chronologie de la lecture réelle. Le suivi de la progression de la lecture du flux pour la gestion des publicités et les analyses vidéo doit utiliser le temps de lecture réel. Le comportement des  et de l’interface utilisateur peut donc ne pas suivre précisément le contenu multimédia et publicitaire.

   * L’agent utilisateur entrant pour toutes les requêtes HTTP de TVSDK sur cette plate-forme est déterminé par le périphérique et la version iOS qui s’exécute sur le périphérique.

      La valeur de la chaîne de l’agent utilisateur correspond par défaut à ce que le système d’exploitation affecte.

## Meilleures pratiques {#section_tvsdk_best_practices}

Voici quelques recommandations pour TVSDK :

* Utilisez HLS version 3.0 ou ultérieure pour le contenu  du.

* Utilisez l’outil Mediastreamvalidator d’Apple pour valider les flux VOD.

* La classe PTSDKConfig fournit des méthodes pour appliquer SSL sur les requêtes effectuées sur les serveurs Primetime et de prise de décision, DRM et Video Analytics.

Pour plus d’informations, voir les méthodes forceHTTPS et isForcingHTTPS dans cette classe.

[!IMPORTANT]

Les requêtes envoyées à des domaines tiers tels que les pixels du suivi des publicités, le contenu et les URL des publicités, ainsi que les requêtes similaires ne sont pas modifiées. Il incombe aux fournisseurs de contenu et aux serveurs d’annonces de fournir des URL prises en charge via HTTPS.