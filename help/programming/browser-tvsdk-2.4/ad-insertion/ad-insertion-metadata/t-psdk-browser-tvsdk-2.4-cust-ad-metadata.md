---
description: Vous pouvez personnaliser les métadonnées d’insertion publicitaire.
seo-description: Vous pouvez personnaliser les métadonnées d’insertion publicitaire.
seo-title: Personnalisation des métadonnées d’insertion publicitaire
title: Personnalisation des métadonnées d’insertion publicitaire
uuid: 047470d3-45bd-48be-82ce-4e9d9fe6ea10
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Personnalisation des métadonnées d’insertion publicitaire{#customize-ad-insertion-metadata}

Vous pouvez personnaliser les métadonnées d’insertion publicitaire.

1. Définissez un délai d’expiration sur les métadonnées publicitaires pour les opportunités non résolues.

   La valeur par défaut de ce délai d’attente est de 20 secondes.
1. Pour modifier la valeur en 10 secondes, saisissez ce qui suit :

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   La `timeout` propriété est définie dans la `AdvertisingMetadata` classe et ce délai peut être défini pour tous les paramètres publicitaires personnalisés qui proviennent de la `AdvertisingMetadata` classe. Par exemple, si les utilisateurs définissent des paramètres personnalisés pour un résolveur FreeWheel, ils peuvent définir un délai d’expiration par défaut en utilisant ce paramètre.

1. Créez `MediaPlayerItemConfig` avec les paramètres de publicité de l’étape 2.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. Utilisez cette configuration lorsque vous appelez `replaceCurrentResource` le `MediaPlayer`.

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```

