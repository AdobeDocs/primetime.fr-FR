---
description: TVSDK prépare les objets PTTimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
title: S’abonner à des balises personnalisées
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 2%

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
