---
description: Vous pouvez configurer un contrôle d’interface utilisateur pour régler le volume de la vidéo.
seo-description: Vous pouvez configurer un contrôle d’interface utilisateur pour régler le volume de la vidéo.
seo-title: Contrôler le volume
title: Contrôler le volume
uuid: f1e959e0-1817-4ccb-8adc-3eba09c91887
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Contrôler le volume {#provide-volume-control}

Vous pouvez configurer un contrôle d’interface utilisateur pour régler le volume de la vidéo.

1. Dans la routine de rappel pour l&#39;élément d&#39;interface de contrôle du volume, vérifiez que le lecteur est dans un état valide pour cette commande.

   >[!TIP]
   >
   >Tout état, à l’exception de RELEASED, est valide.

1. Appelez `setVolume` pour définir le volume audio.

   Par exemple :

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   La valeur du volume représente le volume demandé exprimé en proportion du volume maximal, où `0` est silencieux et `1` est le volume maximal.

