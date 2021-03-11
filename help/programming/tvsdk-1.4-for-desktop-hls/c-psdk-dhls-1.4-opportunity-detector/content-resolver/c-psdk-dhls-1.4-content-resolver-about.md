---
description: TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans la chronologie, et ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d'une période de panne.
title: Générateurs d’opportunités et résolveurs de contenu
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# Générateurs d&#39;opportunités et résolveurs de contenu{#opportunity-generators-and-content-resolvers}

TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans la chronologie, et ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut avoir besoin de modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d&#39;une période de panne.

Un *`opportunity`* représente un point d’intérêt sur la chronologie qui indique généralement une opportunité d’emplacement publicitaire. Cette opportunité peut également indiquer une opération personnalisée qui pourrait affecter la chronologie, telle qu’une période d’interruption. Un *`opportunity generator`* identifie les opportunités spécifiques (balises) dans la chronologie et avertit TVSDK que ces opportunités ont été balisées. Les opportunités sont identifiées dans un calendrier dans `TimedMetadata`. `SpliceOutOpportunityGenerator` crée des opportunités en fonction des objets `TimedMetadata` créés pour chaque balise d&#39;annonce détectée dans le manifeste, et `AdSignalingModeOpportunityGenerator` crée l&#39;opportunité initiale basée sur le type `MediaPlayerItem` et son mode de signalisation publicitaire associé.

Lorsque votre application est informée d&#39;une opportunité (balise), elle peut modifier la chronologie en insérant, par exemple, une série de publicités, en passant à un autre flux (coupures de courant) ou en modifiant le contenu de la chronologie. Par défaut, TVSDK appelle le *`content resolver`* approprié pour mettre en oeuvre les modifications ou actions de chronologie requises. Votre application peut utiliser le programme de résolution de contenu publicitaire par défaut TVSDK ou enregistrer son propre programme de résolution de contenu.

Vous pouvez également utiliser `PSDKConfig.adTags` pour ajouter d’autres balises/signaux de marqueurs publicitaires pour la classe `SpliceOutOpportunityGenerator` par défaut et utiliser `PSDKConfig.setSubscribedTags` pour que TVSDK puisse avertir votre application des balises supplémentaires susceptibles d’avoir des informations de flux de travaux publicitaires.

Une utilisation possible d&#39;un résolveur personnalisé est pour les périodes d&#39;interruption. Pour gérer ces périodes, votre application pourrait mettre en oeuvre et enregistrer un détecteur d&#39;opportunité de panne qui est responsable de la gestion des balises de panne. Lorsque TVSDK rencontre cette balise, il sonde tous les contenus enregistrés afin de trouver le premier qui traite la balise spécifiée. Dans cet exemple, il s’agit du résolveur de contenu d’interruption, qui peut, par exemple, remplacer l’élément actif par un contenu alternatif sur le lecteur pendant la durée spécifiée par la balise .
