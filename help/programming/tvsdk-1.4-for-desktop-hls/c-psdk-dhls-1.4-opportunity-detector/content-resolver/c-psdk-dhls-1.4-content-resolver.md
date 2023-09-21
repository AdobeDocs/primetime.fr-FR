---
description: Un détecteur d’opportunités est un composant TVADK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le workflow d’insertion de contenu/de publicité en fonction des propriétés et des métadonnées de l’opportunité de placement.
title: Personnalisation des détecteurs d’opportunités et des programmes de résolution de contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Présentation {#customize-opportunity-detectors-and-content-resolvers-overiew}

Un détecteur d’opportunités est un composant TVADK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le workflow d’insertion de contenu/de publicité en fonction des propriétés et des métadonnées de l’opportunité de placement.

TVSDK comprend des détecteurs d’opportunités par défaut :

* `SpliceOutOpportunityDetector`, qui comprend les indices publicitaires par défaut
* `AdSignalingModeOpportunityGenerator`, responsable de la création des opportunités de placement publicitaire initiales en fonction du mode de signalisation publicitaire.
* `SpliceOutOpportunityGenerator`, responsable de la création d’opportunités de placement publicitaire à partir de n’importe quelle balise #EXT-X-CUE

TVSDK comprend également un résolveur de contenu par défaut qui fournit du contenu à insérer en fonction de la clé de métadonnées dans l’élément de lecteur :

* `AuditudeResolver`, capable de communiquer avec les serveurs de prise de décision publicitaire Adobe Primetime (précédemment appelés Auditude) et de renvoyer des coupures publicitaires à placer.

Vous pouvez remplacer les détecteurs d’opportunité et les résolveurs de contenu par défaut pour personnaliser le workflow publicitaire comme suit :

* Ajout de la prise en charge de la détection de balises personnalisée
* Reconnaissance des balises personnalisées pour l’insertion de publicités
* Création d’un fournisseur d’annonces personnalisé
* Contenu en noir
