---
description: La propriété MediaPlayerItem.timedMetadata vous donne accès à tous les objets TimedMetadata créés à partir des balises playlist/manifest ou ID3 dans le flux multimédia. La propriété MediaPlayerItem.hasTimedMetadata indique si une balise personnalisée abonnée est présente dans le média actuel.
title: Notifications des balises manifestes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Notifications des balises manifestes{#notifications-for-manifest-tags}

La propriété MediaPlayerItem.timedMetadata vous donne accès à tous les objets TimedMetadata créés à partir des balises playlist/manifest ou ID3 dans le flux multimédia. La propriété MediaPlayerItem.hasTimedMetadata indique si une balise personnalisée abonnée est présente dans le média actuel.

Vous pouvez surveiller les métadonnées minutées en écoutant les événements suivants, qui notifient votre application de l’activité associée :

* `MediaPlayerItemEvent.ITEM_CREATED`: la liste initiale de `TimedMetadata` est disponible après la `MediaPlayerItem` est créée. Cet événement avertit votre application lorsque cela se produit.

* `MediaPlayerItemEvent.ITEM_UPDATED`: pour les flux en direct/linéaires où la liste de lecture/manifeste s’actualise régulièrement, d’autres balises personnalisées peuvent apparaître dans la liste de lecture/manifeste mise à jour, de sorte que des objets TimedMetadata supplémentaires peuvent être ajoutés à la variable `MediaPlayerItem.timedMetadata` . Cet événement avertit votre application lorsque cela se produit.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: chaque fois qu’une nouvelle `TimedMetadata` est créé, cet événement est distribué par la fonction `MediaPlayer`. Cet événement n’est pas distribué pour la variable `TimedMetadata` créé lors de la phase d’initialisation.
