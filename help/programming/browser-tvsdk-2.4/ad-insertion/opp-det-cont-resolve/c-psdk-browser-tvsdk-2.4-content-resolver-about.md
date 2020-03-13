---
description: Le navigateur TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans le plan de montage chronologique. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application doit peut-être modifier la chronologie en fonction des opportunités identifiées dans le manifeste.
seo-description: Le navigateur TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans le plan de montage chronologique. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application doit peut-être modifier la chronologie en fonction des opportunités identifiées dans le manifeste.
seo-title: Générateurs d’opportunités et résolveurs de contenu
title: Générateurs d’opportunités et résolveurs de contenu
uuid: e462ad89-1609-4efa-aa67-cfd04f045927
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Générateurs d’opportunités et résolveurs de contenu{#opportunity-generators-and-content-resolvers}

Le navigateur TVSDK fournit des générateurs d’opportunités et des résolveurs de contenu par défaut qui placent des publicités dans le plan de montage chronologique. Ces générateurs et résolveurs sont basés sur des balises non standard dans le manifeste. Votre application doit peut-être modifier la chronologie en fonction des opportunités identifiées dans le manifeste.

Un *`opportunity`* représente un point d’intérêt sur le plan de montage chronologique qui indique généralement une opportunité de placement d’annonce. Cette opportunité peut également indiquer une opération personnalisée qui pourrait affecter le plan de montage chronologique. Une *`opportunity generator`* page identifie les opportunités spécifiques (balises) dans la chronologie et avertit TVSDK que ces opportunités ont été balisées.

Les opportunités sont identifiées dans un calendrier dans `TimedMetata`. Le `ManifestCuesOpportunityGenerator` crée des opportunités en fonction des `TimedMetadata` objets créés pour chaque balise publicitaire de division (in `MediaPlayerItemConfig.adTags`) détectée dans le manifeste. Le `AdSignalingModeOpportunityGenerator` créera la première opportunité basée sur le `MediaPlayerItem` type et le mode de signalisation publicitaire associé.

>[!TIP]
>
>Si la `AdvertisingMetadata.livePreroll` ou la `AdvertisingMetadata.preroll` propriété est définie, `AdSignalingModeOpportunityGenerator` génère une opportunité de pré-lecture pour les flux en direct.

Lorsque votre application est avertie d’une opportunité (balise), elle peut modifier la chronologie en insérant, par exemple, une série de publicités. Par défaut, le navigateur TVSDK appelle le lecteur approprié *`content resolver`* pour mettre en oeuvre les modifications ou actions requises de la chronologie. Votre application peut utiliser le programme de résolution de contenu publicitaire par défaut du navigateur TVSDK ou enregistrer son propre programme de résolution de contenu.

Vous pouvez également utiliser `MediaPlayerItemConfig.adTags` pour ajouter d’autres balises/signaux de marqueurs publicitaires pour la `ManifestCuesOpportunityGenerator` classe par défaut et `MediaPlayerItemConfig.subscribedTags` pour que TVSDK puisse avertir votre application des balises supplémentaires susceptibles d’avoir des informations sur le processus publicitaire.

>[!TIP]
>
>Les valeurs par défaut de `MediaPlayerItemConfig.adTags` et `MediaPlayerItemConfig.subscribeTags` sont `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`.

