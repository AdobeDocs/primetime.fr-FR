---
description: Ces classes fournissent des métadonnées pour la publicité, les espaces de nommage et le suivi.
title: Classes de métadonnées
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# Classes de métadonnées {#metadata-classes}

Ces classes fournissent des métadonnées pour la publicité, les espaces de nommage et le suivi.

Package : [com.adobe.mediacore.metadata](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/metadata/package-detail.html)

| Nom | Description |
|---|---|
| [AdSignalingMode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/metadata/AdSignalingMode.html) | Classe de énumération exposant les modes de signalisation pris en charge dans l&#39;expression. |
| [ParamètresAuditude](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/metadata/AuditudeSettings.html) | Classe qui étend `Metadata` spécifiquement pour Expression. Fournit des propriétés à configurer pour la résolution des publicités par expression pour un élément multimédia donné. Vous devez définir toutes les propriétés requises, y compris l’ID de zone, l’ID de média et l’URL du serveur d’annonces, pour configurer le lecteur en vue d’une résolution des publicités réussie. |
| [ByteArrayMetadata](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/metadata/ByteArrayMetadata.html) | Déconseillé. Utilisez `Metadata`. |
| [DefaultMetadataKeys](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/metadata/DefaultMetadataKeys.html) | Classe. |
| [Métadonnées](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/metadata/Metadata.html) | Définit l’interface générique de configuration de toutes les métadonnées disponibles pour votre lecteur et les objets supplémentaires. |
| [MetadataNode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/metadata/MetadataNode.html) | Déconseillé. Utilisez `Metadata`. |
| [MetadataUtils](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/metadata/MetadataUtils.html) | Classe des méthodes d’utilisation des métadonnées. |
| [TimedMetadata](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/metadata/TimedMetadata.html) | Classe pour la représentation brute des métadonnées minutées insérées dans un flux média. |
| [TimedMetadataType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/metadata/TimedMetadataType.html) | Classe contenant les types pris en charge pour les métadonnées minutées (dans la liste de lecture ou le flux), telles que les métadonnées ID3 ou les balises. |