---
description: Utilisez la fonction Browserify library files fournie par Browser TVSDK dans votre application pour créer un lecteur compatible Browserify à l’aide de l’interface utilisateur-Framework.
title: Création d’un lecteur compatible avec la fonction Browserify à l’aide de l’interface utilisateur-Framework
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Création d’un lecteur compatible avec la fonction Browserify à l’aide de l’interface utilisateur-Framework {#create-a-browserify-compatible-player-using-the-ui-framework}

Utilisez la fonction Browserify library files fournie par Browser TVSDK dans votre application pour créer un lecteur compatible Browserify à l’aide de l’interface utilisateur-Framework.

Exemples de fichiers Browserify inclus dans le TVSDK :

* [!DNL [..]/samples/browserify/ui-framework/build/Gruntfile.js]
* [!DNL [..]/samples/browserify/ui-framework/build/package.json]
* [!DNL [..]/samples/browserify/ui-framework/examples/sample.html]
* [!DNL [..]/samples/browserify/ui-framework/examples/sample.js]

Pour créer une application compatible avec le navigateur à l’aide de l’interface utilisateur-Framework, vous devez `require` les deux modules Browserify (fournis par le Browser TVSDK) dans le code de votre application :

1. Require Browserify modules :

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. Poursuivez le développement comme décrit dans la section [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md).
>Vous pouvez désormais regrouper vos fichiers d’application à l’aide de Browserify.
