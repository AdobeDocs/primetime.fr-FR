---
description: TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.
title: Abonnement à des balises personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Abonnement à des balises personnalisées{#subscribe-to-custom-tags}

TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le manifeste de contenu.

Avant de commencer la lecture, vous devez vous abonner aux balises .
Pour vous abonner aux balises, affectez un vecteur contenant les noms de balise personnalisés au `subscribedTags` . Si vous devez également modifier les balises d’annonce utilisées par le générateur d’opportunités par défaut, affectez un vecteur contenant les noms de balise d’annonce personnalisés à la variable `adTags` .

Pour être averti des balises personnalisées dans les manifestes HLS :

1. Définissez globalement les noms des balises d’annonces personnalisées en attribuant un vecteur contenant les balises personnalisées à `subscribeTags` in `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >Vous devez inclure la variable `#` préfixe lors de l’utilisation des flux HLS.

   Par exemple :

   ```
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   PSDKConfig.subscribedTags = subscribedTags;
   ```

1. Pour modifier globalement les balises d’annonce utilisées par le générateur d’opportunités par défaut, affectez un vecteur contenant les noms de balises d’annonce personnalisés à la variable `adTags` dans `PSDKConfig`.

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   PSDKConfig.adTags = adTags; 
   ```

1. Pour que tous les paramètres globaux prennent effet, remplacez la ressource actuelle.

   ```
   player.replaceCurrentResource(mediaResource);
   ```

1. Pour définir les noms des balises abonnées d’un flux, le cas échéant :
   1. Créez une configuration d’élément du lecteur multimédia.

      >[!TIP]
      >
      >La méthode la plus simple consiste à créer une configuration d’élément de lecteur multimédia par défaut.

   1. Attribuer un vecteur contenant des balises personnalisées à `subscribeTags` in `MediaPlayerItemConfig`.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     new DefaultMediaPlayerItemConfig(); 
   
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.subscribeTags = subscribedTags;
   ```

1. Pour modifier les balises d’annonce utilisées par le générateur d’opportunités par défaut dans le flux spécifié, affectez un vecteur contenant les noms de balise d’annonce personnalisés au `adTags` dans `mediaPlayerItemConfig`

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Pour que les modifications du flux prennent effet, lors du chargement du flux multimédia, utilisez la configuration de l’élément du lecteur multimédia.

   ```
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```
