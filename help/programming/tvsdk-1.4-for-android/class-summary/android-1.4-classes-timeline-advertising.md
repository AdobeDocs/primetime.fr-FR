---
description: Ces classes fournissent des informations sur les publicités qui se produisent dans un plan de montage chronologique.
seo-description: Ces classes fournissent des informations sur les publicités qui se produisent dans un plan de montage chronologique.
seo-title: Classes publicitaires du journal
title: Classes publicitaires du journal
uuid: 4e6ca9fb-9e68-4625-a24b-386a50333862
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Classes publicitaires du journal{#timeline-advertising-classes}

Ces classes fournissent des informations sur les publicités qui se produisent dans un plan de montage chronologique.

Package : [com.adobe.mediacore.timeline.publicités](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/package-summary.html)

Package : [com.adobe.mediacore.timeline.publicité.auditude](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/package-summary.html)

| Nom | Description |
|--- |--- |
| [Publicité](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Classe qui définit l’abstraction de la publicité et contient toutes les informations de la publicité. Elle est définie par un identifiant unique, une durée et un `MediaResource`. Le `MediaResource` contient l&#39;URL où réside le contenu réel de la publicité. |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | Classe qui représente un fichier à afficher. Classe représentant une ressource publicitaire. |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | Classe qui donne un  unifié sur plusieurs publicités qui seront lues à un moment donné pendant la lecture. |
| [AdBreakPlacement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPlacement.html) | Classe d&#39;opération de placement des coupures publicitaires. |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPolicy.html) |  qui définit la stratégie de lecture des publicités liée au contournement des publicités par l’utilisateur lors de la recherche. |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | Classe qui représente une instance de clic associée à une ressource. Cette instance contient des informations sur l’URL de clic publicitaire et le titre qui peuvent être utilisés pour fournir des informations supplémentaires à l’utilisateur. |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicyInfo.html) | Interface qui définit les propriétés des appels d’API AdPolicySelector. Ces propriétés fournissent le contexte pour appliquer chaque comportement publicitaire. |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicySelector.html) | Interface de sélecteur de stratégies publicitaires pour appliquer des comportements publicitaires. Les applications peuvent se conformer à cette interface en implémentant toutes les méthodes requises ou en étendant la classe de sélecteur de stratégie par défaut existante pour personnaliser des comportements spécifiques. |
| `auditude.AuditudeAdProvider` | Déconseillé. Utilisez AuditudeResolver. |
| [AuditudeResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeResolver.html) | Classe qui gère la résolution des publicités avant l’heure dans le processus Expression. |
| [AuditudeTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeTracker.html) | Classe qui implémente l’interface ContentTracker et définit le  de suivi des publicités Primetime. |
| [ContentResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentResolver.html) | Classe qui gère la partie de résolution publicitaire dans le processus Expression. |
| [ContentTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentTracker.html) | Interface qui définit le protocole que vous devez implémenter si vous souhaitez créer un module de suivi des publicités conçu pour s’intégrer à la bibliothèque ou à un outil de suivi des publicités personnalisé. Cette interface requiert que vous définissiez la manière dont les  de progression des publicités sont rapportées au système de suivi des publicités distant. |
| [PlacementInformation](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/PlacementInformation.html) | Classe qui extrait une demande d’informations de placement. Chaque publicité résolue doit comporter une information d’emplacement. Les informations de placement indiquent où la publicité est destinée à être placée dans le plan de montage chronologique. Il contient des informations telles que : <ul><li>Position de placement (en ms) </li><li>Type de placement (pré-roulage, mid-roll ou post-roll) </li><li>Durée du bloc de contenu principal sur le point d&#39;être remplacé</li></ul> |
