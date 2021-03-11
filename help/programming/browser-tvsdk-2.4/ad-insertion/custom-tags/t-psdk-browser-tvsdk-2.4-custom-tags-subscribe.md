---
description: Le navigateur TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont détectés dans le fichier MPD (Media Presentation Description).
title: S’abonner à des balises publicitaires personnalisées
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# S’abonner à des balises publicitaires personnalisées{#subscribe-to-custom-ad-tags}

Le navigateur TVSDK prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont détectés dans le fichier MPD (Media Presentation Description).

Vous devez vous abonner aux balises avant les débuts de lecture.
Pour vous abonner à des balises, définissez un vecteur contenant les noms de balise personnalisés sur la propriété `subscribedTags`. Si vous devez également modifier les balises publicitaires utilisées par le générateur d’opportunités par défaut, définissez un vecteur contenant les noms de balises publicitaires personnalisées sur la propriété `adTags`.

Pour vous abonner à des balises personnalisées :

1. Créez une configuration d’élément du lecteur multimédia.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
   ```

1. Créez un vecteur de chaîne vide.

   ```js
   var subscribeTags = [];
   ```

1. Ajoutez les noms des balises personnalisées sur ce vecteur.

   >[!IMPORTANT]
   >
   >Si vous traitez de flux HLS, n&#39;oubliez pas d&#39;inclure le préfixe `#`.

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. Affectez le vecteur mis à jour à la propriété `mediaPlayerItemConfig.subscribeTags`.

   ```js
   mediaPlayerItemConfig.subscribeTags = subscribeTags;
   ```

1. Créez un vecteur de chaîne vide.

   ```js
   var adTags= [];
   ```

1. Ajoutez le nom de la balise d&#39;annonce personnalisée sur ce vecteur.

   ```js
   adTags.push("urn:com:adobe:dpi:simple:2015");
   ```

1. Affectez le vecteur mis à jour à la propriété `mediaPlayerItemConfig.adTags`.

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Utilisez la configuration d’élément du lecteur multimédia lors du chargement du flux média.

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```

