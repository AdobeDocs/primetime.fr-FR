---
description: La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux multimédia.
title: Notifications des balises manifestes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Notifications des balises manifestes{#notifications-for-manifest-tags}

La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux multimédia.

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

La variable `MediaPlayerItem.hasTimedMetadata` indique si une balise personnalisée abonnée existe dans le média actuel. Vous pouvez surveiller les métadonnées minutées en écoutant les `Events.TimedMetadataEvent`, que l’instance MediaPlayer distribue chaque fois qu’une nouvelle `TimedMetadata` est créé.
