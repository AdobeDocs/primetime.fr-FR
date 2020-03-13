---
description: La propriété MediaPlayerItem.timedMetadata vous donne accès à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’identifiants3 dans le flux média. La propriété MediaPlayerItem.hasTimedMetadata indique si une balise personnalisée abonnée est présente dans le média actuel.
seo-description: La propriété MediaPlayerItem.timedMetadata vous donne accès à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’identifiants3 dans le flux média. La propriété MediaPlayerItem.hasTimedMetadata indique si une balise personnalisée abonnée est présente dans le média actuel.
seo-title: Notifications pour les balises de manifeste
title: Notifications pour les balises de manifeste
uuid: 87bee41b-b44e-4d12-afd2-7a63023f992c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Notifications pour les balises de manifeste{#notifications-for-manifest-tags}

La propriété MediaPlayerItem.timedMetadata vous donne accès à tous les objets TimedMetadata créés à partir de balises playlist/manifest ou d’identifiants3 dans le flux média. La propriété MediaPlayerItem.hasTimedMetadata indique si une balise personnalisée abonnée est présente dans le média actuel.

Vous pouvez surveiller les métadonnées minutées en écoutant les  de suivantes, qui avertissent votre application des  de connexes :

* `MediaPlayerItemEvent.ITEM_CREATED`: Le initial des `TimedMetadata` objets est disponible une fois `MediaPlayerItem` créé. Ce avertit votre application lorsque cela se produit.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Dans le cas des flux en direct/linéaires dans lesquels le manifeste/la liste de lecture est régulièrement actualisé, d’autres balises personnalisées peuvent apparaître dans la liste de lecture/le manifeste mis à jour, de sorte que d’autres objets TimedMetadata peuvent être ajoutés à la `MediaPlayerItem.timedMetadata` propriété. Ce avertit votre application lorsque cela se produit.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Chaque fois qu’un nouvel `TimedMetadata` objet est créé, ce  de est distribué par le `MediaPlayer`. Ce n’est pas distribué pour l’ `TimedMetadata` objet créé pendant la phase d’initialisation.

