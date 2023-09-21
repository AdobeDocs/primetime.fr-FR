---
description: Vous pouvez configurer un contrôle de l’interface utilisateur pour régler le volume de la vidéo.
title: Contrôle du volume
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Contrôle du volume {#provide-volume-control}

Vous pouvez configurer un contrôle de l’interface utilisateur pour régler le volume de la vidéo.

1. Dans la routine de rappel de l’élément d’interface de contrôle du volume, assurez-vous que le lecteur est dans un état valide pour cette commande.

   >[!TIP]
   >
   >Tout état, sauf RELEASED, est valide.

1. Appeler `setVolume` pour définir le volume audio.

   Par exemple :

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   La valeur du volume représente le volume demandé exprimé en proportion du volume maximal, où `0` est silencieux et `1` est le volume maximal.
