---
description: Vous pouvez configurer une commande de l’interface utilisateur pour le volume sonore.
title: Contrôle du volume
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Contrôle du volume{#provide-volume-control}

Vous pouvez configurer une commande de l’interface utilisateur pour le volume sonore.

1. Attendez que l’instance MediaPlayer soit dans un état valide pour cette commande, à l’exception de RELEASED ou ERROR.
1. Appeler `setVolume` sur le `MediaPlayer` pour définir le volume audio.

   ```java
   void setVolume(int volume) throws IllegalStateException;
   ```

   La valeur du volume représente le volume demandé exprimé en proportion du volume maximum, où 0 est silencieux et 100 est le volume maximum.
