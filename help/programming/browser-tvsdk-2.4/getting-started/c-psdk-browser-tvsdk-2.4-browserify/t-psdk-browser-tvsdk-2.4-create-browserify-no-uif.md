---
description: Utilisez le fichier de bibliothèque Browserify fourni par le navigateur TVSDK dans votre application pour créer un lecteur compatible avec le navigateur.
seo-description: Utilisez le fichier de bibliothèque Browserify fourni par le navigateur TVSDK dans votre application pour créer un lecteur compatible avec le navigateur.
seo-title: Création d’un lecteur compatible avec les navigateurs sans interface utilisateur-cadre
title: Création d’un lecteur compatible avec les navigateurs sans interface utilisateur-cadre
uuid: c4315bc8-c75d-4dd9-8680-946c1197be1e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Créez un lecteur compatible avec les navigateurs sans interface utilisateur-Framework{#create-a-browserify-compatible-player-without-the-ui-framework}

Utilisez le fichier de bibliothèque Browserify fourni par le navigateur TVSDK dans votre application pour créer un lecteur compatible avec le navigateur.

La rubrique [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) liste l’ensemble de bibliothèques du navigateur TVSDK que vous incluez normalement lors de la création d’un lecteur vidéo de base. Pour ce faire, il vous suffit d&#39;ajouter des balises `script` avec des attributs `src` pointant vers les bibliothèques.

Le processus diffère légèrement pour la création d’un lecteur compatible avec le navigateur. Pour ce faire, vous utilisez la commande `require` pour inclure le fichier [!DNL AdobePSDK.module.js] (fourni par le navigateur TVSDK) dans votre application. Ce fichier regroupe les fichiers de base de la bibliothèque du lecteur dans leur ordre de dépendance approprié et renvoie l&#39;espace de nommage `AdobePSDK` que vous utilisez pour implémenter les fonctionnalités de votre lecteur.

Le navigateur TVSDK fournit l’exemple suivant d’application Browserify et crée des fichiers dans le package de version :

* [ !DNL [...]/samples/browserify/reference/build/Gruntfile.js]
* [ !DNL [...]/samples/browserify/reference/build/package.json]
* [ !DNL [...]/samples/browserify/reference/examples/sample.html]
* [ !DNL [...]/samples/browserify/reference/examples/sample.js]

Pour créer un lecteur vidéo compatible avec la fonction de navigation :

1. Exigez le fichier de bibliothèque compatible avec le navigateur qui renvoie l&#39;espace de nommage `AdobePSDK` :

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. Créez votre lecteur comme décrit dans [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md).

   L’étape 1 de cette tâche remplace l’étape des instructions de base du lecteur dans laquelle vous sources les bibliothèques de base individuelles du lecteur dans votre fichier d’application.
Vous pouvez désormais regrouper vos fichiers d’application à l’aide de Browserify.
