---
description: Ces classes fournissent des informations sur les publicités qui se produisent dans une chronologie.
title: Classes publicitaires de journal
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Classes publicitaires de journal {#timeline-advertising-classes}

Ces classes fournissent des informations sur les publicités qui se produisent dans une chronologie.

Package : [com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/package-detail.html)
Package : [com.adobe.mediacore.timeline.advertising.policy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/package-detail.html)

| Nom | Description |
|---|---|
| [Publicité](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Classe qui définit l’abstraction de la publicité et contient toutes les informations sur la publicité. Elle est définie par un identifiant unique, une durée et une `MediaResource`. La variable `MediaResource` contient l’URL où réside le contenu réel de la publicité. |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | Classe qui représente une ressource à afficher. Classe représentant une ressource publicitaire. |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | Classe qui offre une vue unifiée sur plusieurs publicités qui seront lues à un moment donné pendant la lecture. |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakPolicy.html) | Énumération qui définit la stratégie de lecture de la publicité associée à l’utilisateur qui contourne les publicités lors de la recherche. |
| [AdBreakTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreakTimelineItem.html) | Élément de chronologie associé à la coupure publicitaire spécifique. |
| [AdBreakWatchedPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakWatchedPolicy.html) | Classe d’énumération pour les stratégies possibles sur le moment où marquer une coupure publicitaire comme ayant été visionnée. |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | Classe qui représente une instance de clic associée à une ressource. Cette instance contient des informations sur l’URL du clic publicitaire et le titre qui peuvent être utilisés pour fournir des informations supplémentaires à l’utilisateur. |
| [AdPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicy.html) | Classe d’énumération pour les stratégies possibles sur l’emplacement où reprendre la lecture d’une coupure publicitaire après la recherche ou le mode de relecture. |
| [AdPolicyMode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicyMode.html) | Classe d’énumération répertoriant les méthodes de lecture du lecteur, telles que la recherche ou la lecture normale. |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | Interface qui définit les propriétés de `AdPolicySelector` Appels API. Ces propriétés fournissent le contexte pour appliquer chaque comportement publicitaire. |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | Interface du sélecteur de stratégie publicitaire permettant d’appliquer des comportements publicitaires. Les applications peuvent se conformer à cette interface en implémentant toutes les méthodes requises ou en étendant la classe de sélecteur de stratégie par défaut existante pour personnaliser des comportements spécifiques. |
| [AdTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdTimelineItem.html) | Élément de chronologie associé à une publicité spécifique. |
| [AuditudeAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AuditudeAdResolver.html) | Classe qui gère la résolution des publicités avant l’heure dans le processus TVSDK. |
| [AdType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdType.html) | Énumération de tous les types d’annonces pris en charge par TVSDK. |
| [MetadataAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/MetadataAdResolver.html) | Classe. |
