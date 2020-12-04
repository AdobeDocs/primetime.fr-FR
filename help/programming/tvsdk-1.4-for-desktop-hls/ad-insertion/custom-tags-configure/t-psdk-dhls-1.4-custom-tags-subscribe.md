---
description: TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
seo-description: TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
seo-title: S’abonner à des balises personnalisées
title: S’abonner à des balises personnalisées
uuid: 43480265-4951-466a-a347-6debfb6935ee
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# S’abonner à des balises personnalisées{#subscribe-to-custom-tags}

TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.

Avant les débuts de lecture, vous devez vous abonner aux balises .
Pour vous abonner à des balises, affectez un vecteur contenant les noms de balise personnalisés à la propriété `subscribedTags`. Si vous devez également modifier les balises publicitaires utilisées par le générateur d&#39;opportunités par défaut, affectez un vecteur contenant les noms de balises publicitaires personnalisées à la propriété `adTags`.

Pour être averti des balises personnalisées dans les manifestes HLS :

1. Définissez les noms des balises publicitaires personnalisées globalement en affectant un vecteur qui contient les balises personnalisées à `subscribeTags` dans `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >Vous devez inclure le préfixe `#` lorsque vous utilisez des flux HLS.

   Par exemple :

   ```
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   PSDKConfig.subscribedTags = subscribedTags;
   ```

1. Pour modifier globalement les balises publicitaires utilisées par le générateur d&#39;opportunités par défaut, affectez un vecteur contenant les noms de balises publicitaires personnalisées à la propriété `adTags` dans `PSDKConfig`.

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   PSDKConfig.adTags = adTags; 
   ```

1. Pour que tous les paramètres globaux prennent effet, remplacez la ressource actuelle.

   ```
   player.replaceCurrentResource(mediaResource);
   ```

1. Si nécessaire, pour définir les noms des balises abonnées pour un flux :
   1. Créez une configuration d’élément du lecteur multimédia.

      >[!TIP]
      >
      >La méthode la plus simple consiste à créer une configuration d’élément par défaut du lecteur multimédia.

   1. Affectez un vecteur contenant les balises personnalisées à `subscribeTags` dans `MediaPlayerItemConfig`.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     new DefaultMediaPlayerItemConfig(); 
   
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.subscribeTags = subscribedTags;
   ```

1. Pour modifier les balises publicitaires utilisées par le générateur d&#39;opportunités par défaut dans le flux spécifié, affectez un vecteur contenant les noms de balises publicitaires personnalisées à la propriété `adTags` dans `mediaPlayerItemConfig`

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Pour que les modifications du flux prennent effet, utilisez la configuration d’élément du lecteur multimédia lors du chargement du flux.

   ```
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

