---
description: TVSDK prépare les objets PTTimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
title: Abonnement à des balises personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Abonnement à des balises personnalisées {#subscribe-to-custom-tags}

TVSDK prépare les objets PTTimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.

Avant de commencer la lecture, vous devez vous abonner aux balises .
Pour être averti des balises personnalisées dans les manifestes HLS :

1. Définissez globalement les noms des balises d’annonces personnalisées en transmettant un tableau contenant les balises personnalisées à `setSubscribedTags` in `PTSDKConfig`.

   >[!IMPORTANT]
   >
   >Vous devez inclure la variable `#` préfixe lors de l’utilisation des flux HLS.

   Par exemple :

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```
