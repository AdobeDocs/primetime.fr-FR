---
description: Vous pouvez configurer un contrôle d’interface utilisateur pour régler le volume de la vidéo.
title: Contrôler le volume
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 2%

---


# Fournir un contrôle de volume {#provide-volume-control}

Vous pouvez configurer un contrôle d’interface utilisateur pour régler le volume de la vidéo.

1. Dans la routine de rappel pour l&#39;élément d&#39;interface de contrôle de volume, assurez-vous que le lecteur est dans un état valide pour cette commande.

   >[!TIP]
   >
   >Tout état, à l’exception de RELEASED, est valide.

1. Appelez `setVolume` pour définir le volume audio.

   Par exemple :

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   La valeur du volume représente le volume demandé exprimé en proportion du volume maximal, où `0` est silencieux et `1` est le volume maximal.