---
description: Ces classes fournissent des informations sur les publicités qui surviennent dans un plan de montage chronologique.
seo-description: Ces classes fournissent des informations sur les publicités qui surviennent dans un plan de montage chronologique.
seo-title: Classes publicitaires de la chronologie
title: Classes publicitaires de la chronologie
uuid: 4e6ca9fb-9e68-4625-a24b-386a50333862
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Classes publicitaires de la chronologie{#timeline-advertising-classes}

Ces classes fournissent des informations sur les publicités qui surviennent dans un plan de montage chronologique.

Package : [com.adobe.mediacore.timeline.publicités](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/package-summary.html)

Package : [com.adobe.mediacore.timeline.publicite.auditude](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/package-summary.html)

| Nom | Description |
|--- |--- |
| [Publicité](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Classe qui définit l’abstraction de la publicité et contient toutes les informations sur la publicité. Il est défini par un identifiant unique, une durée et un `MediaResource`identifiant. Le `MediaResource` contient l&#39;URL où réside le contenu de la publicité. |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | Classe qui représente une ressource à afficher. Classe représentant une ressource publicitaire. |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | Classe qui donne une vue unifiée sur plusieurs publicités qui seront lues à un moment donné pendant la lecture. |
| [AdBreakPlacement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPlacement.html) | Classe d&#39;opération de placement de coupure publicitaire. |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPolicy.html) | Énumération qui définit la stratégie de lecture des publicités associée au contournement des publicités par l’utilisateur lors de la recherche. |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | Classe qui représente une instance de clic associée à une ressource. Cette instance contient des informations sur l’URL de clic publicitaire et le titre qui peuvent être utilisés pour fournir des informations supplémentaires à l’utilisateur. |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicyInfo.html) | Interface qui définit les propriétés des appels d’API AdPolicySelector. Ces propriétés fournissent le contexte pour appliquer chaque comportement publicitaire. |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicySelector.html) | Interface de sélecteur de stratégies publicitaires pour appliquer des comportements publicitaires. Les applications peuvent se conformer à cette interface en implémentant toutes les méthodes requises ou en étendant la classe de sélecteur de stratégies par défaut existante pour personnaliser des comportements spécifiques. |
| `auditude.AuditudeAdProvider` | Déconseillé. Utilisez AuditudeResolver. |
| [AuditudeResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeResolver.html) | Classe qui gère l&#39;heure de début et la résolution dans le processus Expression. |
| [AuditudeTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeTracker.html) | Classe qui implémente l&#39;interface ContentTracker et définit les événements de suivi publicitaire Primetime. |
| [ContentResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentResolver.html) | Classe qui gère la partie de résolution publicitaire dans le processus Expression. |
| [ContentTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentTracker.html) | Interface qui définit le protocole que vous devez implémenter si vous souhaitez créer un module de suivi publicitaire conçu pour s’intégrer à la bibliothèque ou à un outil de suivi publicitaire personnalisé. Cette interface requiert que vous définissiez la manière dont les événements de progression de la publicité sont signalés au système de suivi des publicités distant. |
| [PlacementInformation](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/PlacementInformation.html) | Classe qui extrait une demande d&#39;informations de placement. Chaque publicité résolue doit être associée à une information d&#39;emplacement. Les informations d’emplacement indiquent où la publicité doit être placée dans la chronologie. Il contient des informations telles que : <ul><li>Position de placement (en ms) </li><li>Type de placement (pré-roulement, mi-roulement ou post-roulement) </li><li>Durée du bloc de contenu principal sur le point d&#39;être remplacé</li></ul> |
