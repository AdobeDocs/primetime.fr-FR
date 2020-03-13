---
description: Un générateur d’opportunités identifie les opportunités de placement par des balises personnalisées dans un flux, des marqueurs personnalisés en mode de signalisation, etc. Le générateur d’opportunités envoie ces opportunités de placement au résolveur de contenu, qui personnalise le flux de travaux d’insertion de contenu/publicité en fonction des propriétés et des métadonnées de l’opportunité de placement.
seo-description: Un générateur d’opportunités identifie les opportunités de placement par des balises personnalisées dans un flux, des marqueurs personnalisés en mode de signalisation, etc. Le générateur d’opportunités envoie ces opportunités de placement au résolveur de contenu, qui personnalise le flux de travaux d’insertion de contenu/publicité en fonction des propriétés et des métadonnées de l’opportunité de placement.
seo-title: Personnalisation des générateurs d’opportunités et des résolveurs de contenu
title: Personnalisation des générateurs d’opportunités et des résolveurs de contenu
uuid: 97738b80-5cf8-494f-8811-449bceded220
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#customize-opportunity-generators-and-content-resolvers-overview}

Un générateur d’opportunités identifie les opportunités de placement par des balises personnalisées dans un flux, des marqueurs personnalisés en mode de signalisation, etc. Le générateur d’opportunités envoie ces opportunités de placement au résolveur de contenu, qui personnalise le flux de travaux d’insertion de contenu/publicité en fonction des propriétés et des métadonnées de l’opportunité de placement.

TVSDK inclut les générateurs d’opportunités par défaut suivants :

* `ManifestCuesOpportunityGenerator` génère des opportunités à partir des indices publicitaires par défaut ( `#EXT-X-CUE`).

* `AdSignalingModeOpportunityGenerator` génère une opportunité initiale pour le mode de signalisation publicitaire spécifié. Cela ignore les indices ou les informations de métadonnées minutées.
* `CustomMarkerOpportunityGenerator` génère des opportunités pour remplacer les publicités C3 intégrées.
* `AuditudeResolver`Le générateur d&#39;opportunités génère des opportunités lorsque la paresse et la résolution sont activées.

TVSDK inclut également des résolutions de contenu par défaut :

* `CustomRangeResolver`
* `JSONResolver`
* `AuditudeResolver`, qui peut communiquer avec Primetime et la prise de décision publicitaire.

Vous pouvez remplacer les générateurs d’opportunités et les résolveurs de contenu par défaut pour personnaliser le flux de travaux publicitaires de différentes manières, telles que :

* Reconnaître les balises personnalisées pour l’insertion de publicités
* Créez un fournisseur d&#39;annonces personnalisé.
* Noircir le contenu.