---
description: Ces classes fournissent des informations sur les publicités qui surviennent dans un plan de montage chronologique.
seo-description: Ces classes fournissent des informations sur les publicités qui surviennent dans un plan de montage chronologique.
seo-title: Classes publicitaires de la chronologie
title: Classes publicitaires de la chronologie
uuid: f424fa13-778b-458d-bc82-389441a8a56a
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Classes publicitaires de la chronologie {#timeline-advertising-classes}

Ces classes fournissent des informations sur les publicités qui surviennent dans un plan de montage chronologique.

Package : [com.adobe.mediacore.timeline.publicités](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/package-detail.html)Package : [com.adobe.mediacore.timeline.publicite.policy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/package-detail.html)

| Nom | Description |
|---|---|
| [Publicité](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Classe qui définit l’abstraction de la publicité et contient toutes les informations sur la publicité. Il est défini par un identifiant unique, une durée et un `MediaResource`identifiant. Le `MediaResource` contient l&#39;URL où réside le contenu de la publicité. |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | Classe qui représente une ressource à afficher. Classe représentant une ressource publicitaire. |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | Classe qui donne une vue unifiée sur plusieurs publicités qui seront lues à un moment donné pendant la lecture. |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakPolicy.html) | Énumération qui définit la stratégie de lecture des publicités associée au contournement des publicités par l’utilisateur lors de la recherche. |
| [AdBreakTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreakTimelineItem.html) | Elément de journal associé à la coupure publicitaire spécifique. |
| [AdBreakWatchedPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakWatchedPolicy.html) | classe de Énumération pour les stratégies possibles sur le moment où marquer une coupure publicitaire comme ayant été regardée. |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | Classe qui représente une instance de clic associée à une ressource. Cette instance contient des informations sur l’URL de clic publicitaire et le titre qui peuvent être utilisés pour fournir des informations supplémentaires à l’utilisateur. |
| [AdPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicy.html) | classe de Énumération pour les stratégies possibles sur l’emplacement où reprendre la lecture d’une coupure publicitaire après la recherche ou le mode de lecture par piège. |
| [AdPolicyMode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicyMode.html) | Classe de Énumération qui liste les méthodes de lecture du lecteur, telles que la recherche ou la lecture normale. |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | Interface qui définit les propriétés des appels d’ `AdPolicySelector` API. Ces propriétés fournissent le contexte pour appliquer chaque comportement publicitaire. |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | Interface de sélecteur de stratégies publicitaires pour appliquer des comportements publicitaires. Les applications peuvent se conformer à cette interface en implémentant toutes les méthodes requises ou en étendant la classe de sélecteur de stratégies par défaut existante pour personnaliser des comportements spécifiques. |
| [AdTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdTimelineItem.html) | Elément de journal associé à une publicité spécifique. |
| [AuditudeAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AuditudeAdResolver.html) | Classe qui gère la résolution des publicités avant la date de début dans le processus TVSDK. |
| [AdType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdType.html) | Énumération de tous les types d’annonces pris en charge par TVSDK. |
| [MetadataAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/MetadataAdResolver.html) | Classe. |

