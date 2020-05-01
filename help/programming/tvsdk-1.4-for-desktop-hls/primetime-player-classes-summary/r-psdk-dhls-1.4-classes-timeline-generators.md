---
description: Ces classes permettent de détecter les opportunités de placement de contenu dans une chronologie, telles que les publicités.
seo-description: Ces classes permettent de détecter les opportunités de placement de contenu dans une chronologie, telles que les publicités.
seo-title: Classes des générateurs de chronologie
title: Classes des générateurs de chronologie
uuid: 1e36b738-0684-44f0-b3c3-dd656c70f705
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Classes des générateurs de chronologie{#timeline-generators-classes}

Ces classes permettent de détecter les opportunités de placement de contenu dans une chronologie, telles que les publicités.

Package : [com.adobe.mediacore.timeline.generators](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/package-detail.html)

| Nom | Description |
|---|---|
| [AdSignalingModeOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/AdSignalingModeOpportunityGenerator.html) | Classe qui crée une opportunité initiale pour le mode de signalisation publicitaire spécifié. |
| [OpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGenerator.html) | Classe de base pour tous les générateurs d&#39;opportunités. |
| [OpportunityGeneratorClient](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGeneratorClient.html) | Interface utilisée par les générateurs d’opportunités pour communiquer avec les composants TVSDK. |
| [SpliceOutOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/SpliceOutOpportunityGenerator.html) | Classe qui surveille la chronologie de la lecture et détecte les opportunités de placement publicitaire insérées dans le manifeste sous forme de commentaires SpliceOut. |
| [TimedMetadataOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/TimedMetadataOpportunityGenerator.html) | Implémentation par défaut d’un générateur d’opportunités qui utilise des métadonnées temporisées pour détecter et générer des opportunités de publicité. |