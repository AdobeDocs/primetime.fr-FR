---
description: Vous pouvez configurer un contrôle d'interface utilisateur pour le volume sonore.
seo-description: Vous pouvez configurer un contrôle d'interface utilisateur pour le volume sonore.
seo-title: Contrôler le volume
title: Contrôler le volume
uuid: 5f2f69cc-3969-4ca2-8ab9-5713fdf5cdb8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Contrôler le volume{#provide-volume-control}

Vous pouvez configurer un contrôle d&#39;interface utilisateur pour le volume sonore.

1. Attendez que l&#39; `MediaPlayer` instance soit dans un état valide pour cette commande.

   Tout état sauf RELEASED ou ERROR est valide.
1. Définissez l&#39;attribut de volume sur l&#39; `MediaPlayer` instance pour définir le volume audio.

   ```js
   player.volume = ...
   ```

   La valeur du volume représente le volume demandé exprimé en proportion du volume maximal, où 0 est silencieux et est le volume maximal.

