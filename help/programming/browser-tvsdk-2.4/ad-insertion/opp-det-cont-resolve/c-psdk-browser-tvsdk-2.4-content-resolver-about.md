---
description: Le navigateur TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans la chronologie. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application doit peut-être modifier le calendrier en fonction des opportunités identifiées dans le manifeste.
title: Générateurs d’opportunités et résolveurs de contenu
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# Générateurs d&#39;opportunités et résolveurs de contenu{#opportunity-generators-and-content-resolvers}

Le navigateur TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans la chronologie. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application doit peut-être modifier le calendrier en fonction des opportunités identifiées dans le manifeste.

Un *`opportunity`* représente un point d’intérêt sur la chronologie qui indique généralement une opportunité d’emplacement publicitaire. Cette opportunité peut également indiquer une opération personnalisée qui pourrait affecter la chronologie. Un *`opportunity generator`* identifie les opportunités spécifiques (balises) dans la chronologie et avertit TVSDK que ces opportunités ont été balisées.

Les opportunités sont identifiées dans un calendrier dans `TimedMetata`. `ManifestCuesOpportunityGenerator` crée des opportunités en fonction des objets `TimedMetadata` créés pour chaque balise publicitaire de division (dans `MediaPlayerItemConfig.adTags`) détectée dans le manifeste. `AdSignalingModeOpportunityGenerator` crée l&#39;opportunité initiale basée sur le type `MediaPlayerItem` et son mode de signalisation publicitaire associé.

>[!TIP]
>
>Si la propriété `AdvertisingMetadata.livePreroll` ou `AdvertisingMetadata.preroll` est définie, `AdSignalingModeOpportunityGenerator` génère une opportunité de pré-diffusion pour les flux en direct.

Lorsque votre application est informée d&#39;une opportunité (balise), elle peut modifier la chronologie en insérant, par exemple, une série de publicités. Par défaut, le navigateur TVSDK appelle le *`content resolver`* approprié pour mettre en oeuvre les modifications ou actions de chronologie requises. Votre application peut utiliser le programme de résolution de contenu de publicité par défaut du navigateur TVSDK ou enregistrer son propre programme de résolution de contenu.

Vous pouvez également utiliser `MediaPlayerItemConfig.adTags` pour ajouter d’autres balises/signaux de marqueurs publicitaires pour la classe `ManifestCuesOpportunityGenerator` par défaut et utiliser `MediaPlayerItemConfig.subscribedTags` pour que TVSDK puisse avertir votre application des balises supplémentaires susceptibles d’avoir des informations sur le flux de travaux de publicité.

>[!TIP]
>
>Les valeurs par défaut `MediaPlayerItemConfig.adTags` et `MediaPlayerItemConfig.subscribeTags` sont `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`.

