---
description: La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux média. La propriété MediaPlayerItem.hasTimedMetadata indique si une balise personnalisée abonnée est présente dans le média actuel.
title: Notifications pour les balises de manifeste
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Notifications pour les balises de manifeste {#notifications-for-manifest-tags}

La propriété MediaPlayerItem.timedMetadata permet d’accéder à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’ID3 dans le flux média. La propriété MediaPlayerItem.hasTimedMetadata indique si une balise personnalisée abonnée est présente dans le média actuel.

Vous pouvez surveiller les métadonnées minutées en écoutant les événements suivants, qui avertissent votre application de l’activité associée :

* `MediaPlayerItemEvent.ITEM_CREATED`: La liste initiale des  `TimedMetadata` objets est disponible une fois  `MediaPlayerItem` créée. Ce événement avertit votre application lorsque cela se produit.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Pour les flux en direct/linéaires où le manifeste/la liste de lecture est régulièrement actualisé, d’autres balises personnalisées peuvent apparaître dans la liste de lecture/le manifeste mis à jour, de sorte que d’autres objets TimedMetadata peuvent être ajoutés à la  `MediaPlayerItem.timedMetadata` propriété. Ce événement avertit votre application lorsque cela se produit.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Chaque fois qu’un nouvel  `TimedMetadata` objet est créé, ce événement est distribué par le  `MediaPlayer`. Ce événement n&#39;est pas distribué pour l&#39;objet `TimedMetadata` créé pendant la phase d&#39;initialisation.

