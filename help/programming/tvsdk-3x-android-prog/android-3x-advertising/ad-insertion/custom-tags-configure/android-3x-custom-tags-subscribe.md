---
description: TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
title: Abonnement à des balises personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Abonnement à des balises personnalisées {#subscribe-to-custom-tags}

TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.

Avant de commencer la lecture, vous devez vous abonner aux balises . Pour être averti des balises personnalisées dans les manifestes HLS :

1. Définissez globalement les noms des balises d’annonces personnalisées en transmettant un tableau contenant les balises personnalisées à `setSubscribedTags` in `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >Vous devez inclure la variable `#` préfixe lors de l’utilisation des flux HLS.

   Par exemple :

   ```java
   String[] array = new String[3]; 
   array[0] = "#EXT-X-ASSET"; 
   array[1] = "#EXT-X-BLACKOUT"; 
   array[2] = "#EXT-OATCLS-SCTE35"; 
   MediaPlayerItemConfig.setSubscribedTags(array);
   ```
