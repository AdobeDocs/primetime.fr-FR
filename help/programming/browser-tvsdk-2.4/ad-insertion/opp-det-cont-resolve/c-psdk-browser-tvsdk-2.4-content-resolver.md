---
description: Un détecteur d’opportunités est un composant Browser TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le flux de travaux d’insertion de contenu/publicités en fonction des propriétés et des métadonnées de l’opportunité de placement.
seo-description: Un détecteur d’opportunités est un composant Browser TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le flux de travaux d’insertion de contenu/publicités en fonction des propriétés et des métadonnées de l’opportunité de placement.
seo-title: Personnaliser les détecteurs d'opportunités et les résolveurs de contenu
title: Personnaliser les détecteurs d'opportunités et les résolveurs de contenu
uuid: d4926933-5966-4cd8-8050-c81c5e3c8545
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#customize-opportunity-detectors-and-content-resolvers-overview}

Un détecteur d’opportunités est un composant Browser TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le flux de travaux d’insertion de contenu/publicités en fonction des propriétés et des métadonnées de l’opportunité de placement.

Le SDK du navigateur inclut les détecteurs d’opportunités par défaut suivants :

* `AdSignalingModeOpportunityGenerator`, qui crée des opportunités de placement initial d’annonce en fonction du mode de signalisation publicitaire.
* `ManifestCuesOpportunityGenerator`, ce qui crée des opportunités d’emplacements publicitaires à partir de n’importe quelle balise de division.

Le SDK du navigateur inclut également des résolveurs de contenu par défaut, tels `AuditudeResolver`, qui fournissent le contenu qui sera inséré en fonction de la clé de métadonnées dans l’élément du lecteur. `AuditudeResolver` est capable de communiquer avec les serveurs Adobe Primetime de prise de décision et de renvoyer les coupures publicitaires à placer.

Vous pouvez remplacer les détecteurs d’opportunités et les résolveurs de contenu par défaut pour personnaliser le flux de travaux publicitaires des manières suivantes :

* Prise en charge Ajouter de la détection personnalisée des balises
* Reconnaître les balises personnalisées pour l’insertion de publicités
* Création d’un fournisseur d’annonces personnalisé

