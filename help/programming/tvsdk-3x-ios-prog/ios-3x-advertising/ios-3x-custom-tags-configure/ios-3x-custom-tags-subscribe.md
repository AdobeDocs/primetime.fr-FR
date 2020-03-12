---
description: TVSDK prépare les objets PTTimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
seo-description: TVSDK prépare les objets PTTimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
seo-title: S’abonner à des balises personnalisées
title: S’abonner à des balises personnalisées
uuid: e47076b2-6184-4c20-bae4-ba7ae62cf198
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# S’abonner à des balises personnalisées {#subscribe-to-custom-tags}

TVSDK prépare les objets PTTimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.

Avant de  la lecture, vous devez vous abonner aux balises.
Pour être averti des balises personnalisées dans les manifestes HLS :

1. Définissez les noms des balises publicitaires personnalisées globalement en transmettant un tableau contenant les balises personnalisées à `setSubscribedTags` in `PTSDKConfig`.

   >[!IMPORTANT]
   >
   >Vous devez inclure le `#` préfixe lors de l’utilisation de flux HLS.

   Par exemple :

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```
