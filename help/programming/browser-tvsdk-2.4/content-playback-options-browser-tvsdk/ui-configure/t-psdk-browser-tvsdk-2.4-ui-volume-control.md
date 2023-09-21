---
description: Vous pouvez configurer une commande de l’interface utilisateur pour le volume sonore.
title: Contrôle du volume
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Contrôle du volume{#provide-volume-control}

Vous pouvez configurer une commande de l’interface utilisateur pour le volume sonore.

1. Attendez que la variable `MediaPlayer` pour être dans un état valide pour cette commande.

   Tout état sauf RELEASED ou ERROR est valide.
1. Définissez l’attribut de volume sur le `MediaPlayer` pour définir le volume audio.

   ```js
   player.volume = ...
   ```

   La valeur du volume représente le volume demandé exprimé en proportion du volume maximum, où 0 est silencieux et est le volume maximum.
