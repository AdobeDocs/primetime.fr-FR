---
description: TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans le plan de montage chronologique. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier la chronologie en fonction des opportunités identifiées dans le manifeste, comme les indicateurs d’une période de panne.
seo-description: TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans le plan de montage chronologique. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier la chronologie en fonction des opportunités identifiées dans le manifeste, comme les indicateurs d’une période de panne.
seo-title: Générateurs d’opportunités et résolveurs de contenu
title: Générateurs d’opportunités et résolveurs de contenu
uuid: e1d658eb-cb6c-407d-9163-2dbf62ba1d19
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Générateurs d’opportunités et résolveurs de contenu{#opportunity-generators-and-content-resolvers}

Un détecteur d’opportunités est un composant TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au résolveur de contenu, qui personnalise le flux de travaux d’insertion de contenu/publicités en fonction des propriétés et des métadonnées de l’opportunité de placement.

TVSDK inclut un détecteur d’opportunités par défaut :

* `PTOpportunityResolver`, qui comprend les indices publicitaires par défaut

TVSDK inclut également un résolveur de contenu par défaut qui fournit le contenu à insérer en fonction de la clé de métadonnées dans l’élément du lecteur :

* `PTContentResolver`

Vous pouvez remplacer les détecteurs d’opportunités et les résolveurs de contenu par défaut pour personnaliser le flux de travaux publicitaires des manières suivantes :

* Prise en charge Ajouter de la détection personnalisée des balises
* Reconnaître les balises personnalisées pour l’insertion de publicités
* Création d’un fournisseur d’annonces personnalisé
* Contenu en noir

TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans le plan de montage chronologique. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier la chronologie en fonction des opportunités identifiées dans le manifeste, comme les indicateurs d’une période de panne.

Un *`opportunity`* représente un point d’intérêt sur le plan de montage chronologique qui indique généralement une opportunité de placement d’annonce. Cette opportunité peut également indiquer une opération personnalisée qui pourrait affecter le calendrier, telle qu’une période d’interruption. Une *`opportunity generator`* page identifie les opportunités spécifiques (balises) dans la chronologie et avertit TVSDK que ces opportunités ont été balisées. Les opportunités sont identifiées dans une chronologie en incluant une balise non standard (non HLS) `PTTimedMetadata` .

Lorsque votre application est informée d’une opportunité (balise), elle peut modifier la chronologie en insérant, par exemple, une série d’annonces, en passant à un autre flux (coupures de courant) ou en modifiant le contenu de la chronologie. Par défaut, TVSDK appelle les éléments appropriés *`content resolver`* pour mettre en oeuvre les modifications ou actions requises de la chronologie. Votre application peut utiliser le réducteur de contenu publicitaire par défaut TVSDK ou enregistrer son propre réducteur de contenu.

Vous pouvez également utiliser `PTSDKConfig.setAdTags` pour ajouter d’autres balises/signaux de marqueurs publicitaires afin que TVSDK puisse reconnaître et utiliser `PTSDKConfig.setSubscribedTags` et notifier à votre application des balises supplémentaires susceptibles de contenir des informations de flux de travaux publicitaires.

Un résolveur personnalisé peut être utilisé pour les périodes d’interruption. Pour gérer ces périodes, votre application pourrait mettre en oeuvre et enregistrer un détecteur d’opportunité de panne qui est responsable de la gestion des balises de panne. Lorsque TVSDK rencontre cette balise, il sonde tous les résolveurs de contenu enregistrés pour trouver le premier à traiter la balise spécifiée. Dans cet exemple, il s’agit du résolveur de contenu d’interruption, qui peut, par exemple, remplacer l’élément actif par un contenu alternatif sur le lecteur pendant la durée spécifiée par la balise .
