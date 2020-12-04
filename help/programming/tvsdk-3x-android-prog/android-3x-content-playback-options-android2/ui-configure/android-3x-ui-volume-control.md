---
description: Vous pouvez configurer un contrôle d’interface utilisateur pour régler le volume de la vidéo.
seo-description: Vous pouvez configurer un contrôle d’interface utilisateur pour régler le volume de la vidéo.
seo-title: Contrôler le volume
title: Contrôler le volume
uuid: c87fe656-0329-4c9c-b65b-43be48c77062
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

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