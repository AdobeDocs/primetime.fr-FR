---
description: Vous pouvez configurer un contrôle d’interface utilisateur pour le volume sonore.
seo-description: Vous pouvez configurer un contrôle d’interface utilisateur pour le volume sonore.
seo-title: Contrôler le volume
title: Contrôler le volume
uuid: 63e96424-54d0-4c16-bd94-2366722f752a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Contrôler le volume{#provide-volume-control}

Vous pouvez configurer un contrôle d’interface utilisateur pour le volume sonore.

1. Attendez que l’instance MediaPlayer soit dans un état valide pour cette commande, à l’exception de RELEASED ou ERROR.
1. Appelez `setVolume` l’ `MediaPlayer` instance pour définir le volume audio.

   ```java
   void setVolume(int volume) throws IllegalStateException;
   ```

   La valeur du volume représente le volume demandé exprimé en proportion du volume maximal, où 0 est silencieux et 100 est le volume maximal.

