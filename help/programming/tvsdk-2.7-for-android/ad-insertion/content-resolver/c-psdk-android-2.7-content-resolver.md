---
description: Un générateur d’opportunités identifie les opportunités de placement par balises personnalisées dans un flux, ainsi que les marqueurs personnalisés en mode de signalisation, etc. Le générateur d’opportunités envoie ces opportunités d’emplacement au résolveur de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité d’emplacement.
seo-description: Un générateur d’opportunités identifie les opportunités de placement par balises personnalisées dans un flux, ainsi que les marqueurs personnalisés en mode de signalisation, etc. Le générateur d’opportunités envoie ces opportunités d’emplacement au résolveur de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité d’emplacement.
seo-title: Personnaliser les générateurs d'opportunités et les résolveurs de contenu
title: Personnaliser les générateurs d'opportunités et les résolveurs de contenu
uuid: 97738b80-5cf8-494f-8811-449bceded220
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#customize-opportunity-generators-and-content-resolvers-overview}

Un générateur d’opportunités identifie les opportunités de placement par balises personnalisées dans un flux, ainsi que les marqueurs personnalisés en mode de signalisation, etc. Le générateur d’opportunités envoie ces opportunités d’emplacement au résolveur de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité d’emplacement.

TVSDK comprend les générateurs d’opportunités par défaut suivants :

* `ManifestCuesOpportunityGenerator` génère des opportunités à partir des indices publicitaires par défaut ( `#EXT-X-CUE`).

* `AdSignalingModeOpportunityGenerator` génère une opportunité initiale pour le mode de signalisation publicitaire spécifié. Cela ignore tout indice ou toute information de métadonnées minutées.
* `CustomMarkerOpportunityGenerator` génère des opportunités pour remplacer les publicités C3 intégrées.
* `AuditudeResolver`Le générateur d’opportunités génère des opportunités lorsque la résolution des publicités paresseuses est activée.

TVSDK inclut également des résolveurs de contenu par défaut :

* `CustomRangeResolver`
* `JSONResolver`
* `AuditudeResolver`, qui peut communiquer avec Primetime et la prise de décision publicitaire.

Vous pouvez remplacer les générateurs d’opportunités et les résolveurs de contenu par défaut pour personnaliser le processus publicitaire de différentes manières, telles que :

* Reconnaître les balises personnalisées pour l’insertion de publicités
* Créez un fournisseur d’annonces personnalisé.
* Noircir le contenu.