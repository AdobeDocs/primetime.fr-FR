---
description: TVSDK prépare les objets PTTimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
seo-description: TVSDK prépare les objets PTTimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
seo-title: S’abonner à des balises personnalisées
title: S’abonner à des balises personnalisées
uuid: de66d3db-46d1-485f-9d3a-6e28495bfb13
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 1%

---


# S’abonner à des balises personnalisées {#subscribe-to-custom-tags}

TVSDK prépare les objets PTTimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.

Avant les débuts de lecture, vous devez vous abonner aux balises .
Pour être averti des balises personnalisées dans les manifestes HLS :

1. Définissez les noms des balises publicitaires personnalisées globalement en transmettant un tableau contenant les balises personnalisées à `setSubscribedTags` dans `PTSDKConfig`.

   >[!IMPORTANT]
   >
   >Vous devez inclure le préfixe `#` lorsque vous utilisez des flux HLS.

   Par exemple :

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```

