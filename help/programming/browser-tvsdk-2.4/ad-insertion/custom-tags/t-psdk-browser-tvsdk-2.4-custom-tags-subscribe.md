---
description: Le navigateur TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont détectés dans le fichier MPD (Media Presentation Description).
seo-description: Le navigateur TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont détectés dans le fichier MPD (Media Presentation Description).
seo-title: S’abonner à des balises publicitaires personnalisées
title: S’abonner à des balises publicitaires personnalisées
uuid: 208f61f4-dc33-4363-aa71-878458740a8d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# S’abonner à des balises publicitaires personnalisées{#subscribe-to-custom-ad-tags}

Le navigateur TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont détectés dans le fichier MPD (Media Presentation Description).

Vous devez vous abonner aux balises avant les débuts de lecture.
Pour vous abonner à des balises, définissez un vecteur contenant les noms de balise personnalisés sur la `subscribedTags` propriété. Si vous devez également modifier les balises publicitaires utilisées par le générateur d’opportunités par défaut, définissez un vecteur contenant les noms de balises publicitaires personnalisées sur la `adTags` propriété.

Pour vous abonner à des balises personnalisées :

1. Créez une configuration d’élément du lecteur multimédia.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
   ```

1. Créez un vecteur de chaîne vide.

   ```js
   var subscribeTags = [];
   ```

1. Ajouter les noms des balises personnalisées à ce vecteur.

   >[!IMPORTANT]
   >
   >Si vous traitez de flux HLS, pensez à inclure le `#` préfixe.

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. Affectez le vecteur mis à jour à la `mediaPlayerItemConfig.subscribeTags` propriété.

   ```js
   mediaPlayerItemConfig.subscribeTags = subscribeTags;
   ```

1. Créez un vecteur de chaîne vide.

   ```js
   var adTags= [];
   ```

1. Ajouter le nom de la balise publicitaire personnalisée à ce vecteur.

   ```js
   adTags.push("urn:com:adobe:dpi:simple:2015");
   ```

1. Affectez le vecteur mis à jour à la `mediaPlayerItemConfig.adTags` propriété.

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Utilisez la configuration d’élément du lecteur multimédia lors du chargement du flux média.

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```

