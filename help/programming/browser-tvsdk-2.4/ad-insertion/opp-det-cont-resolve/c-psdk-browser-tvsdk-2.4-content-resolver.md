---
description: Un détecteur d’opportunités est un composant Browser TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au programme de résolution de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité de placement.
title: Personnaliser les détecteurs d'opportunités et les résolveurs de contenu
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# Aperçu {#customize-opportunity-detectors-and-content-resolvers-overview}

Un détecteur d’opportunités est un composant Browser TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au programme de résolution de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité de placement.

Le navigateur TVSDK comprend les détecteurs d’opportunités par défaut suivants :

* `AdSignalingModeOpportunityGenerator`, qui crée des opportunités initiales d’emplacement des publicités en fonction du mode de signalisation des publicités.
* `ManifestCuesOpportunityGenerator`, qui crée des opportunités d’emplacement d’annonce à partir de n’importe quelle balise d’éclatement.

Le navigateur TVSDK comprend également des résolveurs de contenu par défaut, tels que `AuditudeResolver`, qui fournit du contenu qui sera inséré en fonction de la clé de métadonnées de l’élément du lecteur. `AuditudeResolver` est capable de communiquer avec les serveurs de prise de décision des publicités Adobe Primetime et de renvoyer les coupures publicitaires à placer.

Vous pouvez remplacer les détecteurs d’opportunités et les résolveurs de contenu par défaut pour personnaliser le processus de publicité de différentes manières :

* Prise en charge des Ajoutes pour la détection personnalisée des balises
* Reconnaître les balises personnalisées pour l’insertion de publicités
* Créer un fournisseur d’annonces personnalisé

