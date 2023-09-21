---
description: Le TVSDK du navigateur prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le fichier MPD (Media Presentation Description).
title: Abonnement à des balises de publicité personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Abonnement à des balises de publicité personnalisées{#subscribe-to-custom-ad-tags}

Le TVSDK du navigateur prépare les objets TimedMetadata pour les balises abonnées chaque fois que ces objets sont rencontrés dans le fichier MPD (Media Presentation Description).

Vous devez vous abonner aux balises avant que la lecture ne démarre.
Pour vous abonner à des balises, définissez un vecteur contenant les noms de balise personnalisés sur la balise `subscribedTags` . Si vous devez également modifier les balises d’annonce utilisées par le générateur d’opportunités par défaut, définissez un vecteur contenant les noms de balise d’annonce personnalisés sur la variable `adTags` .

Pour vous abonner à des balises personnalisées :

1. Créez une configuration d’élément du lecteur multimédia.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
   ```

1. Créez un vecteur de chaîne vide.

   ```js
   var subscribeTags = [];
   ```

1. Ajoutez les noms de balise personnalisés à ce vecteur.

   >[!IMPORTANT]
   >
   >Si vous avez affaire à des flux HLS, pensez à inclure la variable `#` préfixe.

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. Affectez le vecteur mis à jour au `mediaPlayerItemConfig.subscribeTags` .

   ```js
   mediaPlayerItemConfig.subscribeTags = subscribeTags;
   ```

1. Créez un vecteur de chaîne vide.

   ```js
   var adTags= [];
   ```

1. Ajoutez le nom de balise de publicité personnalisée à ce vecteur.

   ```js
   adTags.push("urn:com:adobe:dpi:simple:2015");
   ```

1. Affectez le vecteur mis à jour au `mediaPlayerItemConfig.adTags` .

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Utilisez la configuration d’élément du lecteur multimédia lors du chargement du flux multimédia.

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```
