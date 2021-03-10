---
description: Utilisez les fichiers de bibliothèque Browserify fournis par le navigateur TVSDK dans votre application pour créer un lecteur compatible Browserify à l’aide de l’interface utilisateur-Framework.
title: Création d’un lecteur compatible avec les navigateurs à l’aide de l’interface utilisateur-Framework
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Créez un lecteur compatible Browserify à l’aide de l’interface utilisateur-Framework {#create-a-browserify-compatible-player-using-the-ui-framework}

Utilisez les fichiers de bibliothèque Browserify fournis par le navigateur TVSDK dans votre application pour créer un lecteur compatible Browserify à l’aide de l’interface utilisateur-Framework.

Exemples de fichiers Browserify inclus dans TVSDK :

* [ !DNL [...]/samples/browserify/ui-framework/build/Gruntfile.js]
* [ !DNL [...]/samples/browserify/ui-framework/build/package.json]
* [ !DNL [...]/samples/browserify/ui-framework/examples/sample.html]
* [ !DNL [...]/samples/browserify/ui-framework/examples/sample.js]

Pour créer une application compatible avec les navigateurs à l’aide de l’interface utilisateur-Framework, vous devez `require` inclure les deux modules Browserify (fournis par le navigateur TVSDK) dans votre code d’application :

1. Require Browserify modules :

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. Procédez au développement comme décrit dans [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md).
>Vous pouvez désormais regrouper vos fichiers d’application à l’aide de Browserify.
