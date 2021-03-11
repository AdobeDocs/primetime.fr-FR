---
description: Vous pouvez configurer un contrôle d'interface utilisateur pour le volume sonore.
title: Contrôler le volume
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---


# Fournir un contrôle de volume{#provide-volume-control}

Vous pouvez configurer un contrôle d&#39;interface utilisateur pour le volume sonore.

1. Attendez que l&#39;instance `MediaPlayer` soit dans un état valide pour cette commande.

   Tout état sauf RELEASED ou ERROR est valide.
1. Définissez l&#39;attribut de volume sur l&#39;instance `MediaPlayer` pour définir le volume audio.

   ```js
   player.volume = ...
   ```

   La valeur du volume représente le volume demandé exprimé en proportion du volume maximal, où 0 est silencieux et est le volume maximal.

