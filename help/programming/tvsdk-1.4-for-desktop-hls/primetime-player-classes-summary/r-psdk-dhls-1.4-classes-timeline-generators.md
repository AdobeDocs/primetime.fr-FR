---
description: Ces classes aident à détecter les opportunités de placement de contenu, telles que les publicités, dans une chronologie.
title: Classes des générateurs de chronologie
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Classes des générateurs de chronologie{#timeline-generators-classes}

Ces classes aident à détecter les opportunités de placement de contenu, telles que les publicités, dans une chronologie.

Package : [com.adobe.mediacore.timeline.generators](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/package-detail.html)

| Nom | Description |
|---|---|
| [AdSignalingModeOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/AdSignalingModeOpportunityGenerator.html) | Classe qui crée une opportunité initiale pour le mode de signalisation publicitaire spécifié. |
| [OpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGenerator.html) | Classe de base pour tous les générateurs d’opportunités. |
| [OpportunityGeneratorClient](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGeneratorClient.html) | Interface utilisée par les générateurs d’opportunités pour communiquer avec les composants TVSDK. |
| [SpliceOutOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/SpliceOutOpportunityGenerator.html) | Classe qui surveille la chronologie de la lecture et détecte les opportunités de placement publicitaire insérées dans le manifeste sous la forme de commentaires SpliceOut. |
| [TimedMetadataOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/TimedMetadataOpportunityGenerator.html) | Mise en oeuvre par défaut d’un générateur d’opportunités qui utilise des informations de métadonnées minutées pour détecter et générer des opportunités de publicité. |
