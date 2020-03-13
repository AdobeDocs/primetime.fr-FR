---
description: Utilisez les fichiers de bibliothèque Browserify fournis par le navigateur TVSDK dans votre application pour créer un lecteur compatible Browserify à l’aide de l’interface utilisateur-Framework.
seo-description: Utilisez les fichiers de bibliothèque Browserify fournis par le navigateur TVSDK dans votre application pour créer un lecteur compatible Browserify à l’aide de l’interface utilisateur-Framework.
seo-title: Création d’un lecteur compatible avec le navigateur à l’aide de UI-Framework
title: Création d’un lecteur compatible avec le navigateur à l’aide de UI-Framework
uuid: 544fd872-5ca1-417d-8aab-69613caada0e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Création d’un lecteur compatible avec le navigateur à l’aide de UI-Framework {#create-a-browserify-compatible-player-using-the-ui-framework}

Utilisez les fichiers de bibliothèque Browserify fournis par le navigateur TVSDK dans votre application pour créer un lecteur compatible Browserify à l’aide de l’interface utilisateur-Framework.

Exemples de fichiers Browserify inclus dans le SDK TVSDK :

* [!DNL [...]/samples/browserify/ui-framework/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/ui-framework/build/package.json]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.html]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.js]

Pour créer une application compatible avec le navigateur à l’aide de l’interface utilisateur-Framework, vous devez `require` disposer des deux modules Browserify (fournis par le SDK du navigateur) dans le code de votre application :

1. Require Browserify modules :

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. Procédez au développement comme décrit dans [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md).
>Vous pouvez désormais regrouper vos fichiers d’application à l’aide de Browserify.
