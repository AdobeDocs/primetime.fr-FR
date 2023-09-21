---
description: Un générateur d’opportunités identifie les opportunités d’emplacement par des balises personnalisées dans un flux, des marqueurs personnalisés en mode de signalement, etc. Le générateur d’opportunités envoie ces opportunités d’emplacement au résolveur de contenu, qui personnalise le workflow d’insertion de contenu/de publicité en fonction des propriétés et des métadonnées de l’opportunité d’emplacement.
title: Personnalisation des générateurs d’opportunités et des résolveurs de contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Présentation {#customize-opportunity-generators-and-content-resolvers-overview}

Un générateur d’opportunités identifie les opportunités d’emplacement par des balises personnalisées dans un flux, des marqueurs personnalisés en mode de signalement, etc. Le générateur d’opportunités envoie ces opportunités d’emplacement au résolveur de contenu, qui personnalise le workflow d’insertion de contenu/de publicité en fonction des propriétés et des métadonnées de l’opportunité d’emplacement.

TVSDK comprend les générateurs d’opportunités par défaut suivants :

* `ManifestCuesOpportunityGenerator` génère des opportunités à partir des signaux publicitaires par défaut ( `#EXT-X-CUE`).

* `AdSignalingModeOpportunityGenerator` génère une opportunité initiale pour le mode de signalisation publicitaire spécifié. Cela ignore les indices ou les informations de métadonnées minutées.
* `CustomMarkerOpportunityGenerator` génère des opportunités pour remplacer les publicités C3 intégrées.
* `AuditudeResolver`Le générateur d’opportunités offre des opportunités lorsque la résolution des publicités paresseuse est activée.

TVSDK comprend également les résolveurs de contenu par défaut :

* `CustomRangeResolver`
* `JSONResolver`
* `AuditudeResolver`, qui peut communiquer avec Primetime et la prise de décision.

Vous pouvez remplacer les générateurs d’opportunités et les résolveurs de contenu par défaut pour personnaliser le workflow publicitaire de la manière suivante :

* Reconnaissez les balises personnalisées pour l’insertion de publicités. Pour plus d’informations, voir [Personnalisation des générateurs d’opportunités et des résolveurs de contenu](../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/content-resolver/android-3x-content-resolver.md).
* Créez un fournisseur d’annonces personnalisé.
* Noircir le contenu.
