---
description: TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans la chronologie, et ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d'une période de panne.
seo-description: TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans la chronologie, et ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d'une période de panne.
seo-title: Générateurs d’opportunités et résolveurs de contenu
title: Générateurs d’opportunités et résolveurs de contenu
uuid: 9eaeeacf-9e7c-4ebb-a91e-fbc53e96d2c3
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Générateurs d’opportunités et résolveurs de contenu{#opportunity-generators-and-content-resolvers}

TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans la chronologie, et ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d&#39;une période de panne.

Un *`opportunity`* représente un point d’intérêt sur la chronologie qui indique généralement une opportunité d’emplacement publicitaire. Cette opportunité peut également indiquer une opération personnalisée qui pourrait affecter la chronologie, telle qu’une période d’interruption. Une *`opportunity generator`* liste identifie les opportunités spécifiques (balises) dans la chronologie et avertit TVSDK que ces opportunités ont été balisées. Les opportunités sont identifiées dans un calendrier dans `TimedMetadata`. Le `SpliceOutOpportunityGenerator` crée des opportunités en fonction des `TimedMetadata` objets créés pour chaque balise publicitaire détectée dans le manifeste et `AdSignalingModeOpportunityGenerator` crée la possibilité initiale basée sur le type `MediaPlayerItem` et son mode de signalisation publicitaire associé.

Lorsque votre application est informée d&#39;une opportunité (balise), elle peut modifier la chronologie en insérant, par exemple, une série de publicités, en passant à un autre flux (coupures de courant) ou en modifiant le contenu de la chronologie. Par défaut, TVSDK appelle les éléments appropriés *`content resolver`* pour mettre en oeuvre les modifications ou actions requises de la chronologie. Votre application peut utiliser le programme de résolution de contenu publicitaire par défaut TVSDK ou enregistrer son propre programme de résolution de contenu.

Vous pouvez également utiliser `PSDKConfig.adTags` pour ajouter d’autres balises/signaux de marqueurs publicitaires pour la `SpliceOutOpportunityGenerator` classe par défaut et utiliser `PSDKConfig.setSubscribedTags` ainsi TVSDK pour avertir votre application des balises supplémentaires susceptibles d’avoir des informations sur le flux de travail publicitaire.

Une utilisation possible d&#39;un résolveur personnalisé est pour les périodes d&#39;interruption. Pour gérer ces périodes, votre application pourrait mettre en oeuvre et enregistrer un détecteur d&#39;opportunité de panne qui est responsable de la gestion des balises de panne. Lorsque TVSDK rencontre cette balise, il sonde tous les contenus enregistrés afin de trouver le premier qui traite la balise spécifiée. Dans cet exemple, il s’agit du résolveur de contenu d’interruption, qui peut, par exemple, remplacer l’élément actif par un contenu alternatif sur le lecteur pendant la durée spécifiée par la balise .
