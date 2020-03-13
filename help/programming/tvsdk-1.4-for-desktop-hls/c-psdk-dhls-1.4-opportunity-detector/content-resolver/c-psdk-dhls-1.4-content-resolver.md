---
description: Un détecteur d’opportunités est un composant TVADK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le flux de travaux d’insertion de contenu/publicités en fonction des propriétés et des métadonnées de l’opportunité de placement.
seo-description: Un détecteur d’opportunités est un composant TVADK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le flux de travaux d’insertion de contenu/publicités en fonction des propriétés et des métadonnées de l’opportunité de placement.
seo-title: Personnaliser les détecteurs d'opportunités et les résolveurs de contenu
title: Personnaliser les détecteurs d'opportunités et les résolveurs de contenu
uuid: 7bd04c8f-6f04-4321-88e8-9bb93251d940
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Présentation {#customize-opportunity-detectors-and-content-resolvers-overiew}

Un détecteur d’opportunités est un composant TVADK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le flux de travaux d’insertion de contenu/publicités en fonction des propriétés et des métadonnées de l’opportunité de placement.

TVSDK inclut des détecteurs d’opportunités par défaut :

* `SpliceOutOpportunityDetector`, qui comprend les indices publicitaires par défaut
* `AdSignalingModeOpportunityGenerator`, qui est chargé de créer des opportunités de placement initial d’annonce en fonction du mode de signalisation publicitaire
* `SpliceOutOpportunityGenerator`, qui est chargé de créer des opportunités d&#39;emplacements publicitaires à partir de n&#39;importe quelle balise #EXT-X-CUE

TVSDK inclut également un résolveur de contenu par défaut qui fournit le contenu à insérer en fonction de la clé de métadonnées dans l’élément du lecteur :

* `AuditudeResolver`, capable de communiquer avec les serveurs de prise de décision publicitaire Adobe Primetime (précédemment appelés Auditude) et de renvoyer les coupures publicitaires à placer.

Vous pouvez remplacer les détecteurs d’opportunités et les résolveurs de contenu par défaut pour personnaliser le flux de travaux publicitaires des manières suivantes :

* Prise en charge Ajouter de la détection personnalisée des balises
* Reconnaître les balises personnalisées pour l’insertion de publicités
* Création d’un fournisseur d’annonces personnalisé
* Contenu en noir

