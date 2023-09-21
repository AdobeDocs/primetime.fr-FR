---
description: TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent les publicités dans la chronologie. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut devoir modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d'une période de blackout.
title: Générateurs d’opportunités et programmes de résolution de contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Générateurs d’opportunités et programmes de résolution de contenu{#opportunity-generators-and-content-resolvers}

TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent les publicités dans la chronologie. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application peut devoir modifier le calendrier en fonction des opportunités identifiées dans le manifeste, telles que les indicateurs d&#39;une période de blackout.

Un *`opportunity`* représente un point ciblé sur la chronologie qui indique généralement une opportunité d’emplacement publicitaire. Cette opportunité peut également indiquer une opération personnalisée qui peut affecter la chronologie, comme une période d’interruption. Un *`opportunity generator`* identifie les opportunités (balises) spécifiques dans la chronologie et informe TVSDK que ces opportunités ont été balisées. Les opportunités sont identifiées dans une chronologie dans `TimedMetadata`. La variable `SpliceOutOpportunityGenerator` crée des opportunités en fonction de la variable `TimedMetadata` les objets créés pour chaque balise publicitaire qui a été détectée dans le manifeste, et la variable `AdSignalingModeOpportunityGenerator` crée l’opportunité initiale basée sur la variable `MediaPlayerItem` type et son mode de signalétique de publicité associé.

Lorsque votre application est avertie d’une opportunité (balise), elle peut modifier la chronologie en insérant, par exemple, une série de publicités, en passant à un autre flux (coupures) ou en modifiant le contenu de la chronologie. Par défaut, TVSDK appelle la *`content resolver`* pour mettre en oeuvre les modifications ou actions de chronologie requises. Votre application peut utiliser le résolveur de contenu publicitaire par défaut de TVSDK ou enregistrer son propre résolveur de contenu.

Vous pouvez également utiliser `PSDKConfig.adTags` pour ajouter d’autres balises/repères de marque publicitaire pour la valeur par défaut `SpliceOutOpportunityGenerator` classe et utilisation `PSDKConfig.setSubscribedTags` afin que TVSDK puisse informer votre application des balises supplémentaires pouvant contenir des informations de workflow publicitaire.

Un résolveur personnalisé peut être utilisé pour les périodes d’interruption. Pour gérer ces périodes, votre application peut mettre en oeuvre et enregistrer un détecteur d’opportunités d’blackout responsable de la gestion des balises d’arrêt. Lorsque TVSDK rencontre cette balise, il interroge tous les programmes de résolution de contenu enregistrés pour trouver le premier qui gère la balise spécifiée. Dans cet exemple, il s’agit du programme de résolution de contenu en blackout, qui peut, par exemple, remplacer l’élément actuel par du contenu alternatif sur le lecteur pendant la durée spécifiée par la balise .
