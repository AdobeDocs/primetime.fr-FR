---
description: Utilisez le fichier de bibliothèque Browserify fourni par le navigateur TVSDK dans votre application pour créer un lecteur compatible avec le navigateur.
seo-description: Utilisez le fichier de bibliothèque Browserify fourni par le navigateur TVSDK dans votre application pour créer un lecteur compatible avec le navigateur.
seo-title: Création d’un lecteur compatible avec le navigateur sans interface utilisateur-cadre
title: Création d’un lecteur compatible avec le navigateur sans interface utilisateur-cadre
uuid: c4315bc8-c75d-4dd9-8680-946c1197be1e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Création d’un lecteur compatible avec le navigateur sans interface utilisateur-cadre{#create-a-browserify-compatible-player-without-the-ui-framework}

Utilisez le fichier de bibliothèque Browserify fourni par le navigateur TVSDK dans votre application pour créer un lecteur compatible avec le navigateur.

La rubrique [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) l’ensemble des bibliothèques du navigateur TVSDK que vous incluez normalement lors de la création d’un lecteur vidéo de base. Pour ce faire, il vous suffit d’ajouter `script` des balises avec `src` des attributs pointant vers les bibliothèques.

Le processus diffère légèrement pour la création d’un lecteur compatible avec le navigateur. Pour cela, vous utilisez la `require` commande pour inclure le [!DNL AdobePSDK.module.js] fichier (fourni par le navigateur TVSDK) dans votre application. Ce fichier regroupe les fichiers de base de la bibliothèque du lecteur dans leur ordre de dépendance approprié et renvoie le `AdobePSDK` que vous utilisez pour implémenter les fonctionnalités de votre lecteur.

Le navigateur TVSDK fournit l’exemple d’application Browserify et crée des fichiers dans le package de version :

* [!DNL [...]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/reference/build/package.json]
* [!DNL [...]/samples/browserify/reference/examples/sample.html]
* [!DNL [...]/samples/browserify/reference/examples/sample.js]

Pour créer un lecteur vidéo compatible avec le navigateur :

1. Exigez le fichier de bibliothèque compatible avec le navigateur qui renvoie le   : `AdobePSDK`

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. Créez votre lecteur comme décrit dans [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md).

   L’étape 1 de ce remplace l’étape des instructions de base du lecteur dans laquelle vous sources les bibliothèques de base individuelles du lecteur dans votre fichier d’application.
Vous pouvez désormais regrouper vos fichiers d’application à l’aide de Browserify.
