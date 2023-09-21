---
description: Le navigateur TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent les publicités dans la chronologie. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Il se peut que votre application doive modifier la chronologie en fonction des opportunités identifiées dans le manifeste.
title: Générateurs d’opportunités et programmes de résolution de contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Générateurs d’opportunités et programmes de résolution de contenu{#opportunity-generators-and-content-resolvers}

Le navigateur TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent les publicités dans la chronologie. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Il se peut que votre application doive modifier la chronologie en fonction des opportunités identifiées dans le manifeste.

Un *`opportunity`* représente un point ciblé sur la chronologie qui indique généralement une opportunité d’emplacement publicitaire. Cette opportunité peut également indiquer une opération personnalisée qui peut affecter la chronologie. Un *`opportunity generator`* identifie les opportunités (balises) spécifiques dans la chronologie et informe TVSDK que ces opportunités ont été balisées.

Les opportunités sont identifiées dans une chronologie dans `TimedMetata`. La variable `ManifestCuesOpportunityGenerator` crée des opportunités en fonction de la variable `TimedMetadata` les objets créés pour chaque balise publicitaire de division (dans `MediaPlayerItemConfig.adTags`) qui a été détecté dans le manifeste. La variable `AdSignalingModeOpportunityGenerator` crée l’opportunité initiale basée sur la variable `MediaPlayerItem` type et son mode de signalétique de publicité associé.

>[!TIP]
>
>Si la variable `AdvertisingMetadata.livePreroll` ou le `AdvertisingMetadata.preroll` est définie, `AdSignalingModeOpportunityGenerator` génère une opportunité preroll pour les diffusions en direct.

Lorsque votre application est informée d’une opportunité (balise), elle peut modifier la chronologie en insérant, par exemple, une série de publicités. Par défaut, le navigateur TVSDK appelle le *`content resolver`* pour mettre en oeuvre les modifications ou actions de chronologie requises. Votre application peut utiliser le résolveur de contenu de publicité par défaut Browser TVSDK ou enregistrer son propre résolveur de contenu.

Vous pouvez également utiliser `MediaPlayerItemConfig.adTags` pour ajouter d’autres balises/repères de marque publicitaire pour la valeur par défaut `ManifestCuesOpportunityGenerator` classe et utilisation `MediaPlayerItemConfig.subscribedTags` afin que TVSDK puisse informer votre application des balises supplémentaires pouvant contenir des informations de workflow publicitaire.

>[!TIP]
>
>Les valeurs par défaut de `MediaPlayerItemConfig.adTags` et `MediaPlayerItemConfig.subscribeTags` is `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`.
