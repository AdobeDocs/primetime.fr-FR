---
description: Un détecteur d’opportunités est un composant TVADK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au programme de résolution de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité de placement.
seo-description: Un détecteur d’opportunités est un composant TVADK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au programme de résolution de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité de placement.
seo-title: Personnaliser les détecteurs d'opportunités et les résolveurs de contenu
title: Personnaliser les détecteurs d'opportunités et les résolveurs de contenu
uuid: 7bd04c8f-6f04-4321-88e8-9bb93251d940
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---


# Aperçu {#customize-opportunity-detectors-and-content-resolvers-overiew}

Un détecteur d’opportunités est un composant TVADK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au programme de résolution de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité de placement.

TVSDK inclut des détecteurs d’opportunités par défaut :

* `SpliceOutOpportunityDetector`, qui comprend les indices publicitaires par défaut
* `AdSignalingModeOpportunityGenerator`, qui est chargé de créer les opportunités initiales de placement des publicités en fonction du mode de signalisation des publicités
* `SpliceOutOpportunityGenerator`, qui est chargé de créer des opportunités de placement d&#39;annonce à partir de n&#39;importe quelle balise #EXT-X-CUE

TVSDK inclut également un résolveur de contenu par défaut qui fournit le contenu à insérer en fonction de la clé de métadonnées dans l’élément du lecteur :

* `AuditudeResolver`, capable de communiquer avec les serveurs de prise de décision d’annonce Adobe Primetime (précédemment connus sous le nom d’Auditude) et de renvoyer les coupures publicitaires à placer.

Vous pouvez remplacer les détecteurs d’opportunités et les résolveurs de contenu par défaut pour personnaliser le processus de publicité de différentes manières :

* Prise en charge des Ajoutes pour la détection personnalisée des balises
* Reconnaître les balises personnalisées pour l’insertion de publicités
* Créer un fournisseur d’annonces personnalisé
* Contenu en noir

