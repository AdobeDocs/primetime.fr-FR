---
description: TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
seo-description: TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
seo-title: S’abonner à des balises personnalisées
title: S’abonner à des balises personnalisées
uuid: fe8ba34d-66fc-43bb-b98e-659c1702d1e0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# S’abonner à des balises personnalisées{#subscribe-to-custom-tags}

TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.

Avant de  la lecture, vous devez vous abonner aux balises.
Pour être averti des balises personnalisées dans les manifestes HLS :

Définissez les noms des balises publicitaires personnalisées globalement en transmettant un tableau contenant les balises personnalisées à `setSubscribedTags` in `MediaPlayerItemConfig`.

>[!IMPORTANT]
>
>Vous devez inclure le `#` préfixe lors de l’utilisation de flux HLS.

Par exemple :

```java
String[] array = new String[3]; 
array[0] = "#EXT-X-ASSET"; 
array[1] = "#EXT-X-BLACKOUT"; 
array[2] = "#EXT-OATCLS-SCTE35"; 
MediaPlayerItemConfig.setSubscribedTags(array);
```

