---
description: Ces classes fournissent des métadonnées pour la publicité, les   et le suivi.
seo-description: Ces classes fournissent des métadonnées pour la publicité, les   et le suivi.
seo-title: Classes de métadonnées
title: Classes de métadonnées
uuid: 6d5099c8-d562-4635-9ef0-068cc6fb9f82
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Classes de métadonnées{#metadata-classes}

Ces classes fournissent des métadonnées pour la publicité, les   et le suivi.

Package : [com.adobe.mediacore.metadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/package-summary.html)

| Nom | Description |
|---|---|
| [AdvertisingMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html) | Classe qui fournit des propriétés qui doivent être configurées pour résoudre les publicités d’un élément multimédia donné. Toutes les propriétés requises doivent être définies pour configurer le lecteur afin de résoudre les publicités. |
| AuditudeMetadata | Déconseillé. Utilisez AuditudeSettings. |
| [ParamètresAuditude](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AuditudeSettings.html) | Classe qui étend Java `AdvertisingMetadata` spécifiquement pour Expression. Fournit des propriétés à configurer pour la résolution des publicités par expression pour un élément multimédia donné. Vous devez définir toutes les propriétés requises, y compris l’ID de zone, l’ID de média et l’URL du serveur d’annonces, pour configurer le lecteur en vue d’une résolution des publicités réussie. |
| [Métadonnées](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/Metadata.html) | Définit l’interface générique de configuration de toutes les métadonnées disponibles pour votre lecteur et les objets supplémentaires. |
| [MetadataNode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/MetadataNode.html) | Classe générique de type structure de données pour le stockage de paires clé-valeur arbitraires. |
| [TimedMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html) | Classe correspondant à la représentation brute des métadonnées minutées insérées dans un flux média. |