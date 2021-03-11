---
description: La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux média.
title: Notifications pour les balises de manifeste
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Notifications pour les balises de manifeste {#notifications-for-manifest-tags}

La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux média.

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

La propriété `MediaPlayerItem.hasTimedMetadata` indique si une balise personnalisée abonnée existe dans le média actuel. Vous pouvez surveiller les métadonnées minutées en écoutant `Events.TimedMetadataEvent`, que l’instance MediaPlayer distribue chaque fois qu’un nouvel objet `TimedMetadata` est créé.
