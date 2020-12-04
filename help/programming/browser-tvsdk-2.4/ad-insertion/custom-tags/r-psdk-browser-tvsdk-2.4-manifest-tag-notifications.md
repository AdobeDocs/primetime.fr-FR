---
description: La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux média.
seo-description: La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux média.
seo-title: Notifications pour les balises de manifeste
title: Notifications pour les balises de manifeste
uuid: 50727455-b37b-4e39-8efb-a97de3164074
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Notifications pour les balises de manifeste {#notifications-for-manifest-tags}

La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux média.

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

La propriété `MediaPlayerItem.hasTimedMetadata` indique si une balise personnalisée abonnée existe dans le média actuel. Vous pouvez surveiller les métadonnées minutées en écoutant `Events.TimedMetadataEvent`, que l’instance MediaPlayer distribue chaque fois qu’un nouvel objet `TimedMetadata` est créé.
