---
description: Ces classes fournissent des métadonnées pour la publicité, les espaces de noms et le suivi.
title: Classes de métadonnées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Classes de métadonnées{#metadata-classes}

Ces classes fournissent des métadonnées pour la publicité, les espaces de noms et le suivi.

Package : [com.adobe.mediacore.metadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/package-summary.html)

| Nom | Description |
|---|---|
| [AdvertisingMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html) | Classe qui fournit des propriétés qui doivent être configurées pour résoudre les publicités d’un élément multimédia donné. Toutes les propriétés requises doivent être définies pour configurer le lecteur afin de résoudre les publicités. |
| AuditudeMetadata | Obsolète. Utilisez AuditudeSettings. |
| [AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AuditudeSettings.html) | Classe qui étend Java `AdvertisingMetadata` spécifiquement pour Expression. Fournit des propriétés à configurer pour résoudre les publicités par expression pour un élément multimédia donné. Vous devez définir toutes les propriétés requises, y compris l’ID de zone, l’ID de média et l’URL du serveur de publicités, pour configurer le lecteur en vue d’une résolution des publicités réussie. |
| [Métadonnées](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/Metadata.html) | Définit l’interface générique de configuration de toutes les métadonnées disponibles pour votre lecteur et des objets supplémentaires. |
| [MetadataNode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/MetadataNode.html) | Classe générique de type structure de données pour le stockage de paires clé-valeur arbitraires. |
| [TimedMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html) | Classe pour la représentation brute des métadonnées minutées insérées dans un flux multimédia. |
