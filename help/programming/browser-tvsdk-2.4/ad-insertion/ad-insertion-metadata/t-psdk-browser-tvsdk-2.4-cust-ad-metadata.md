---
description: Vous pouvez personnaliser les métadonnées d’insertion publicitaire.
title: Personnalisation des métadonnées d’insertion publicitaire
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Personnaliser les métadonnées d’insertion de publicités{#customize-ad-insertion-metadata}

Vous pouvez personnaliser les métadonnées d’insertion publicitaire.

1. Définissez un délai d’expiration sur les métadonnées publicitaires pour les opportunités non résolues.

   La valeur par défaut de ce délai d’attente est de 20 secondes.
1. Pour modifier la valeur en 10 secondes, saisissez ce qui suit :

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   La propriété `timeout` est définie dans la classe `AdvertisingMetadata` et ce délai peut être défini pour tous les paramètres publicitaires personnalisés qui dérivent de la classe `AdvertisingMetadata`. Par exemple, si les utilisateurs définissent des paramètres personnalisés pour un résolveur FreeWheel, ils peuvent définir un délai d’expiration par défaut en utilisant ce paramètre.

1. Créez `MediaPlayerItemConfig` avec les paramètres de publicité de l’étape 2.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. Utilisez cette configuration lorsque vous appelez `replaceCurrentResource` sur `MediaPlayer`.

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```

