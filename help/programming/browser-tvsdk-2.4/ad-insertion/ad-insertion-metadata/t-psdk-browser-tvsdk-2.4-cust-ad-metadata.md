---
description: Vous pouvez personnaliser les métadonnées d’insertion de publicités.
title: Personnalisation des métadonnées d’insertion de publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Personnalisation des métadonnées d’insertion de publicités{#customize-ad-insertion-metadata}

Vous pouvez personnaliser les métadonnées d’insertion de publicités.

1. Définissez un délai d’expiration sur les métadonnées publicitaires pour les opportunités non résolues.

   La valeur par défaut de ce délai d’expiration est de 20 secondes.
1. Pour définir la valeur sur 10 secondes, saisissez la valeur suivante :

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   La variable `timeout` est définie dans la variable `AdvertisingMetadata` et ce délai peut être défini pour tout paramètre d’annonce personnalisé qui dérive de la variable `AdvertisingMetadata` classe . Par exemple, si les utilisateurs définissent des paramètres personnalisés pour un programme de résolution FreeWheel, ils peuvent définir un délai d’expiration par défaut à l’aide de ce paramètre.

1. Créer `MediaPlayerItemConfig` avec les paramètres de publicité de l’étape 2.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. Utilisez cette configuration lorsque vous appelez `replaceCurrentResource` on `MediaPlayer`.

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```
