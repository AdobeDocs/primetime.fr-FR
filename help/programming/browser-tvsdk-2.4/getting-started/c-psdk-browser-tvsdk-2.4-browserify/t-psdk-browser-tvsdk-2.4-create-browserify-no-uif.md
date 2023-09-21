---
description: Utilisez le fichier de bibliothèque Browserify fourni par le Browser TVSDK dans votre application pour créer un lecteur compatible Browserify.
title: Création d’un lecteur compatible avec la fonction Browserify sans l’interface utilisateur-Framework
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Création d’un lecteur compatible avec la fonction Browserify sans l’interface utilisateur-Framework{#create-a-browserify-compatible-player-without-the-ui-framework}

Utilisez le fichier de bibliothèque Browserify fourni par le Browser TVSDK dans votre application pour créer un lecteur compatible Browserify.

Le sujet [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) répertorie l’ensemble des bibliothèques TVSDK du navigateur que vous incluez normalement lors de la création d’un lecteur vidéo de base. Pour ce faire, ajoutez simplement `script` balises avec `src` attributs pointant vers les bibliothèques.

Le processus diffère légèrement pour la création d’un lecteur compatible avec Browserify. Pour ce faire, vous utilisez le `require` pour inclure la commande [!DNL AdobePSDK.module.js] (fourni par le Browser TVSDK) dans votre application. Ce fichier regroupe les fichiers de base de la bibliothèque du lecteur dans leur ordre de dépendance approprié, et renvoie la variable `AdobePSDK` espace de noms que vous utilisez pour mettre en oeuvre des fonctionnalités pour votre lecteur.

Le navigateur TVSDK fournit l’exemple d’application Browserify suivant et crée des fichiers dans le package de version :

* [!DNL [..]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [..]/samples/browserify/reference/build/package.json]
* [!DNL [..]/samples/browserify/reference/examples/sample.html]
* [!DNL [..]/samples/browserify/reference/examples/sample.js]

Pour créer un lecteur vidéo compatible avec la fonction Browserify :

1. Requiert le fichier de bibliothèque compatible Browserify qui renvoie la variable `AdobePSDK` namespace :

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. Créez votre lecteur comme décrit dans la section [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md).

   L’étape 1 de cette tâche remplace l’étape des instructions de base du lecteur dans laquelle vous sources les bibliothèques de lecteur de base individuelles dans votre fichier d’application.
Vous pouvez désormais regrouper vos fichiers d’application à l’aide de Browserify.
