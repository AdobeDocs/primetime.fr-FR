---
description: Un détecteur d’opportunités est un composant TVSDK Navigateur qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le workflow d’insertion de contenu/de publicité en fonction des propriétés et des métadonnées de l’opportunité de placement.
title: Personnalisation des détecteurs d’opportunités et des programmes de résolution de contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Présentation {#customize-opportunity-detectors-and-content-resolvers-overview}

Un détecteur d’opportunités est un composant TVSDK Navigateur qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le workflow d’insertion de contenu/de publicité en fonction des propriétés et des métadonnées de l’opportunité de placement.

Le SDK du navigateur comprend les détecteurs d’opportunités par défaut suivants :

* `AdSignalingModeOpportunityGenerator`, qui crée les opportunités initiales de placement publicitaire en fonction du mode de signalisation publicitaire.
* `ManifestCuesOpportunityGenerator`, qui crée des opportunités d’emplacement des publicités à partir de n’importe quelle balise de scission.

Le navigateur TVSDK comprend également des résolveurs de contenu par défaut, tels que `AuditudeResolver`, qui fournit du contenu qui sera inséré en fonction de la clé de métadonnées dans l’élément de lecteur. `AuditudeResolver` peut communiquer avec les serveurs de prise de décision publicitaire Adobe Primetime et renvoyer des coupures publicitaires à placer.

Vous pouvez remplacer les détecteurs d’opportunité et les résolveurs de contenu par défaut pour personnaliser le workflow publicitaire comme suit :

* Ajout de la prise en charge de la détection de balises personnalisée
* Reconnaissance des balises personnalisées pour l’insertion de publicités
* Création d’un fournisseur d’annonces personnalisé
