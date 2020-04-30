---
description: TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
seo-description: TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
seo-title: S’abonner à des balises personnalisées
title: S’abonner à des balises personnalisées
uuid: 9f74b2b9-bbc9-433c-8226-2c2b68eddf7e
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# S’abonner à des balises personnalisées {#subscribe-to-custom-tags}

TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.

Avant les débuts de lecture, vous devez vous abonner aux balises . Pour être averti des balises personnalisées dans les manifestes HLS :

1. Définissez les noms des balises publicitaires personnalisées globalement en transmettant un tableau contenant les balises personnalisées à `setSubscribedTags` entrer `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >Vous devez inclure le `#` préfixe lors de l’utilisation des flux HLS.

   Par exemple :

   ```java
   String[] array = new String[3]; 
   array[0] = "#EXT-X-ASSET"; 
   array[1] = "#EXT-X-BLACKOUT"; 
   array[2] = "#EXT-OATCLS-SCTE35"; 
   MediaPlayerItemConfig.setSubscribedTags(array);
   ```

