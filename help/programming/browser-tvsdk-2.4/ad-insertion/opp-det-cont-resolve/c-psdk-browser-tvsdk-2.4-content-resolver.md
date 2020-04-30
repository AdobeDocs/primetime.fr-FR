---
description: Un détecteur d’opportunités est un composant Browser TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au programme de résolution de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité de placement.
seo-description: Un détecteur d’opportunités est un composant Browser TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au programme de résolution de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité de placement.
seo-title: Personnaliser les détecteurs d'opportunités et les résolveurs de contenu
title: Personnaliser les détecteurs d'opportunités et les résolveurs de contenu
uuid: d4926933-5966-4cd8-8050-c81c5e3c8545
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#customize-opportunity-detectors-and-content-resolvers-overview}

Un détecteur d’opportunités est un composant Browser TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au programme de résolution de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité de placement.

Le navigateur TVSDK comprend les détecteurs d’opportunités par défaut suivants :

* `AdSignalingModeOpportunityGenerator`, qui crée des opportunités initiales d’emplacement des publicités en fonction du mode de signalisation des publicités.
* `ManifestCuesOpportunityGenerator`, qui crée des opportunités d’emplacement d’annonce à partir de n’importe quelle balise d’éclatement.

Le navigateur TVSDK inclut également des résolveurs de contenu par défaut, tels `AuditudeResolver`que, qui fournit du contenu qui sera inséré en fonction de la clé de métadonnées dans l’élément du lecteur. `AuditudeResolver` est capable de communiquer avec les serveurs de prise de décision publicitaire d’Adobe Primetime et de renvoyer les coupures publicitaires à placer.

Vous pouvez remplacer les détecteurs d’opportunités et les résolveurs de contenu par défaut pour personnaliser le processus de publicité de différentes manières :

* Prise en charge Ajouter de la détection personnalisée des balises
* Reconnaître les balises personnalisées pour l’insertion de publicités
* Créer un fournisseur d’annonces personnalisé

