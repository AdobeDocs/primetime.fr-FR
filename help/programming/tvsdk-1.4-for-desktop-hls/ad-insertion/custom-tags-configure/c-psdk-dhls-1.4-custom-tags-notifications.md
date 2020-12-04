---
description: La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux média. La propriété MediaPlayerItem.hasTimedMetadata indique si une balise personnalisée abonnée est présente dans le média actuel.
seo-description: La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux média. La propriété MediaPlayerItem.hasTimedMetadata indique si une balise personnalisée abonnée est présente dans le média actuel.
seo-title: Notifications pour les balises de manifeste
title: Notifications pour les balises de manifeste
uuid: 87bee41b-b44e-4d12-afd2-7a63023f992c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# Notifications pour les balises de manifeste {#notifications-for-manifest-tags}

La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux média. La propriété MediaPlayerItem.hasTimedMetadata indique si une balise personnalisée abonnée est présente dans le média actuel.

Vous pouvez surveiller les métadonnées minutées en écoutant les événements suivants, qui avertissent votre application de l’activité associée :

* `MediaPlayerItemEvent.ITEM_CREATED`: La liste initiale des  `TimedMetadata` objets est disponible une fois  `MediaPlayerItem` créée. Ce événement avertit votre application lorsque cela se produit.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Pour les flux en direct/linéaires où le manifeste/la liste de lecture est régulièrement actualisé, d’autres balises personnalisées peuvent apparaître dans la liste de lecture/le manifeste mis à jour, de sorte que d’autres objets TimedMetadata peuvent être ajoutés à la  `MediaPlayerItem.timedMetadata` propriété. Ce événement avertit votre application lorsque cela se produit.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Chaque fois qu’un nouvel  `TimedMetadata` objet est créé, ce événement est distribué par le  `MediaPlayer`. Ce événement n&#39;est pas distribué pour l&#39;objet `TimedMetadata` créé pendant la phase d&#39;initialisation.

