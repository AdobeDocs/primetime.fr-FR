---
description: TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans la chronologie, et ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d'une période de panne.
seo-description: TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans la chronologie, et ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d'une période de panne.
seo-title: Générateurs d’opportunités et résolveurs de contenu
title: Générateurs d’opportunités et résolveurs de contenu
uuid: e1d658eb-cb6c-407d-9163-2dbf62ba1d19
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# Générateurs d&#39;opportunités et résolveurs de contenu{#opportunity-generators-and-content-resolvers}

Un détecteur d’opportunités est un composant TVSDK qui détecte les balises personnalisées dans un flux et identifie les opportunités de placement. Ces opportunités sont envoyées au programme de résolution de contenu, qui personnalise le processus d’insertion de contenu/publicités en fonction des propriétés et métadonnées de l’opportunité de placement.

TVSDK inclut un détecteur d’opportunités par défaut :

* `PTOpportunityResolver`, qui comprend les indices publicitaires par défaut

TVSDK inclut également un résolveur de contenu par défaut qui fournit le contenu à insérer en fonction de la clé de métadonnées dans l’élément du lecteur :

* `PTContentResolver`

Vous pouvez remplacer les détecteurs d’opportunités et les résolveurs de contenu par défaut pour personnaliser le processus de publicité de différentes manières :

* Prise en charge des Ajoutes pour la détection personnalisée des balises
* Reconnaître les balises personnalisées pour l’insertion de publicités
* Créer un fournisseur d’annonces personnalisé
* Contenu en noir

TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans la chronologie, et ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d&#39;une période de panne.

Un *`opportunity`* représente un point d’intérêt sur la chronologie qui indique généralement une opportunité d’emplacement publicitaire. Cette opportunité peut également indiquer une opération personnalisée qui pourrait affecter la chronologie, telle qu’une période d’interruption. Un *`opportunity generator`* identifie les opportunités spécifiques (balises) dans la chronologie et avertit TVSDK que ces opportunités ont été balisées. Les opportunités sont identifiées dans une chronologie dans `PTTimedMetadata` en incluant une balise non standard (non HLS).

Lorsque votre application est informée d&#39;une opportunité (balise), elle peut modifier la chronologie en insérant, par exemple, une série de publicités, en passant à un autre flux (coupures de courant) ou en modifiant le contenu de la chronologie. Par défaut, TVSDK appelle le *`content resolver`* approprié pour mettre en oeuvre les modifications ou actions de chronologie requises. Votre application peut utiliser le programme de résolution de contenu publicitaire par défaut TVSDK ou enregistrer son propre programme de résolution de contenu.

Vous pouvez également utiliser `PTSDKConfig.setAdTags` pour ajouter d’autres balises/signaux de marqueurs publicitaires afin que TVSDK reconnaisse et utilise `PTSDKConfig.setSubscribedTags` et avertisse votre application des balises supplémentaires susceptibles de contenir des informations de flux de travaux publicitaires.

Une utilisation possible d&#39;un résolveur personnalisé est pour les périodes d&#39;interruption. Pour gérer ces périodes, votre application pourrait mettre en oeuvre et enregistrer un détecteur d&#39;opportunité de panne qui est responsable de la gestion des balises de panne. Lorsque TVSDK rencontre cette balise, il sonde tous les contenus enregistrés afin de trouver le premier qui traite la balise spécifiée. Dans cet exemple, il s’agit du résolveur de contenu d’interruption, qui peut, par exemple, remplacer l’élément actif par un contenu alternatif sur le lecteur pendant la durée spécifiée par la balise .
