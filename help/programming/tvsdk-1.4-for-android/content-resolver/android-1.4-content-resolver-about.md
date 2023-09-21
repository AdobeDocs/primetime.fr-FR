---
description: Un détecteur d’opportunités est un composant TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le workflow d’insertion de contenu/de publicité en fonction des propriétés et des métadonnées de l’opportunité de placement.
title: Générateurs d’opportunités et programmes de résolution de contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# Générateurs d’opportunités et programmes de résolution de contenu {#opportunity-generators-and-content-resolvers}

Un détecteur d’opportunités est un composant TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le workflow d’insertion de contenu/de publicité en fonction des propriétés et des métadonnées de l’opportunité de placement.

TVSDK comprend un détecteur d’opportunités par défaut :

* `SpliceOutPlacementOpportunityDetector`, qui comprend les indices publicitaires par défaut

TVSDK inclut également des résolveurs de contenu par défaut qui fournissent du contenu à insérer en fonction de la clé de métadonnées dans l’élément de lecteur :

* `AuditudeResolver` pour `AUDITUDE_METADATA_KEY`, qui est capable de communiquer avec les serveurs de prise de décision publicitaire Adobe Primetime (précédemment appelés Auditude) et de renvoyer des coupures publicitaires à placer.

* `MetadataResolver` pour `JSON_METADATA_KEY`

* `CustomAdMarkersContentResolver` pour `TIME_RANGES_METADATA_KEY`

Vous pouvez remplacer les détecteurs d’opportunité et les résolveurs de contenu par défaut pour personnaliser le workflow publicitaire comme suit :

* Ajout de la prise en charge de la détection de balises personnalisée
* Reconnaissance des balises personnalisées pour l’insertion de publicités
* Création d’un fournisseur d’annonces personnalisé
* Contenu en noir

TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent les publicités dans la chronologie. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut devoir modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d&#39;une période de blackout.

Un *`opportunity`* représente un point ciblé sur la chronologie qui indique généralement une opportunité d’emplacement publicitaire. Cette opportunité peut également indiquer une opération personnalisée qui peut affecter la chronologie, comme une période d’interruption. Un *`opportunity generator`* identifie les opportunités (balises) spécifiques dans la chronologie et informe TVSDK que ces opportunités ont été balisées. Les opportunités sont identifiées dans une chronologie dans en incluant une balise non standard (non HLS).

Lorsque votre application est avertie d’une opportunité (balise), elle peut modifier la chronologie en insérant, par exemple, une série de publicités, en passant à un autre flux (coupures) ou en modifiant le contenu de la chronologie. Par défaut, TVSDK appelle la *`content resolver`* pour mettre en oeuvre les modifications ou actions de chronologie requises. Votre application peut utiliser le résolveur de contenu publicitaire par défaut de TVSDK ou enregistrer son propre résolveur de contenu.

Vous pouvez également utiliser `MediaPlayerItemConfig.setAdTags` pour ajouter d’autres balises/signaux de marqueurs publicitaires afin que TVSDK puisse reconnaître et utiliser `MediaPlayerItemConfig.subscribedTags` et informez votre application des balises supplémentaires pouvant contenir des informations de workflow publicitaire.

Un résolveur personnalisé peut être utilisé pour les périodes d’interruption. Pour gérer ces périodes, votre application peut mettre en oeuvre et enregistrer un détecteur d’opportunités d’blackout responsable de la gestion des balises d’arrêt. Lorsque TVSDK rencontre cette balise, il interroge tous les programmes de résolution de contenu enregistrés pour trouver le premier qui gère la balise spécifiée. Dans cet exemple, il s’agit du programme de résolution de contenu en blackout, qui peut, par exemple, remplacer l’élément actuel par du contenu alternatif sur le lecteur pendant la durée spécifiée par la balise .
