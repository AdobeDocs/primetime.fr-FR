---
description: Ces classes fournissent des informations sur les publicités qui se produisent dans une chronologie.
title: Classes publicitaires de journal
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Classes publicitaires de journal{#timeline-advertising-classes}

Ces classes fournissent des informations sur les publicités qui se produisent dans une chronologie.

Package : [com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/package-summary.html)

Package : [com.adobe.mediacore.timeline.advertising.auditude](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/package-summary.html)

| Nom | Description |
|--- |--- |
| [Publicité](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Classe qui définit l’abstraction de la publicité et contient toutes les informations sur la publicité. Elle est définie par un identifiant unique, une durée et une `MediaResource`. La variable `MediaResource` contient l’URL où réside le contenu réel de la publicité. |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | Classe qui représente une ressource à afficher. Classe représentant une ressource publicitaire. |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | Classe qui offre une vue unifiée sur plusieurs publicités qui seront lues à un moment donné pendant la lecture. |
| [AdBreakPlacement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPlacement.html) | Classe d’opération de placement de coupure publicitaire. |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPolicy.html) | Énumération qui définit la stratégie de lecture de la publicité associée à l’utilisateur qui contourne les publicités lors de la recherche. |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | Classe qui représente une instance de clic associée à une ressource. Cette instance contient des informations sur l’URL du clic publicitaire et le titre qui peuvent être utilisés pour fournir des informations supplémentaires à l’utilisateur. |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicyInfo.html) | Interface qui définit les propriétés des appels de l’API AdPolicySelector. Ces propriétés fournissent le contexte pour appliquer chaque comportement publicitaire. |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicySelector.html) | Interface du sélecteur de stratégie publicitaire permettant d’appliquer des comportements publicitaires. Les applications peuvent se conformer à cette interface en implémentant toutes les méthodes requises ou en étendant la classe de sélecteur de stratégie par défaut existante pour personnaliser des comportements spécifiques. |
| `auditude.AuditudeAdProvider` | Obsolète. Utilisez AuditudeResolver. |
| [AuditudeResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeResolver.html) | Classe qui gère les heures d’ouverture et la résolution dans le processus Expression. |
| [AuditudeTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeTracker.html) | Classe qui met en oeuvre l’interface ContentTracker et définit les événements de suivi des publicités Primetime. |
| [ContentResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentResolver.html) | Classe qui gère la partie de résolution des publicités dans le processus Expression. |
| [ContentTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentTracker.html) | Interface qui définit le protocole que vous devez implémenter si vous souhaitez créer un module de suivi des publicités conçu pour s’intégrer à la bibliothèque ou à un dispositif de suivi des publicités personnalisé. Cette interface requiert que vous définissiez la manière dont les événements de progression de la publicité sont signalés au système de suivi des publicités distant. |
| [PlacementInformation](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/PlacementInformation.html) | Classe qui extrait une demande d’informations d’emplacement. Chaque publicité résolue doit comporter une information d’emplacement qui lui est associée. Les informations d’emplacement décrivent l’emplacement de la publicité qui doit être placée dans la chronologie. Il contient des informations telles que : <ul><li>Position de l’emplacement (en ms) </li><li>Type de l’emplacement (preroll, mid-roll ou post-roll) </li><li>Durée du bloc de contenu principal sur le point d’être remplacé</li></ul> |
