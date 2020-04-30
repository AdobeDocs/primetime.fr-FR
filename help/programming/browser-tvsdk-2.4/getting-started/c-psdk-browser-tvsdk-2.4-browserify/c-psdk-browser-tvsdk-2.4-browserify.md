---
description: Vous pouvez créer un lecteur compatible avec le navigateur à l’aide de fichiers JS fournis par le navigateur TVSDK.
seo-description: Vous pouvez créer un lecteur compatible avec le navigateur à l’aide de fichiers JS fournis par le navigateur TVSDK.
seo-title: Lecteur compatible avec la navigation
title: Lecteur compatible avec la navigation
uuid: 1832c826-d5d0-41b0-852f-286c8e4fa0f3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#browserify-compatible-player-overview}

Vous pouvez créer un lecteur compatible avec le navigateur à l’aide de fichiers JS fournis par le navigateur TVSDK.

Le navigateur TVSDK fournit deux fichiers JS compatibles avec le navigateur. L’un est destiné au module AdobePSDK ; il s’agit du développement d’applications sans interface utilisateur-Framework. L&#39;autre est destiné au module UI-Framework ; il renvoie l’espace de nommage PTP que vous utilisez pour écrire des applications à l’aide de UI-Framework.

Pour commencer avec Browserify, exécutez les commandes de configuration suivantes pour créer [!DNL final.js] des fichiers (votre fichier d’assemblage Browserify) dans les [!DNL example] répertoires situés sous [!DNL samples/browerify/reference] et [!DNL samples/browerify/ui-framework]:

1. Accédez à [!DNL samples/browserify/reference/build].
1. Exécutez les commandes suivantes :

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. Accédez à [!DNL samples/browserify/ui-framework/build].
1. Exécutez les mêmes commandes que celles de l’étape 2.

Une fois cette configuration terminée, vous pouvez continuer à créer des applications TVSDK compatibles avec les navigateurs en vous basant sur les exemples fournis avec TVSDK.
