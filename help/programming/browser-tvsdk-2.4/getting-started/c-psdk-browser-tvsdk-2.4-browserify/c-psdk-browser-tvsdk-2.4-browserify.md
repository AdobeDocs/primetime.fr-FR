---
description: Vous pouvez créer un lecteur compatible avec le navigateur à l’aide des fichiers JS fournis par le navigateur TVSDK.
seo-description: Vous pouvez créer un lecteur compatible avec le navigateur à l’aide des fichiers JS fournis par le navigateur TVSDK.
seo-title: Lecteur compatible avec les navigateurs
title: Lecteur compatible avec les navigateurs
uuid: 1832c826-d5d0-41b0-852f-286c8e4fa0f3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#browserify-compatible-player-overview}

Vous pouvez créer un lecteur compatible avec le navigateur à l’aide des fichiers JS fournis par le navigateur TVSDK.

Le SDK du navigateur fournit deux fichiers JS compatibles avec le navigateur. L’une est destinée à être utilisée avec le module AdobePSDK ; il s’agit du développement d’applications sans interface utilisateur-cadre. L&#39;autre est à utiliser avec le module UI-Framework ; il renvoie le PTP  que vous utilisez pour écrire des applications à l’aide de UI-Framework.

Pour commencer avec Browserify, exécutez les commandes de configuration suivantes pour créer [!DNL final.js] des fichiers (votre fichier d’assemblage Browserify) dans les [!DNL example] répertoires situés sous [!DNL samples/browerify/reference] et [!DNL samples/browerify/ui-framework]:

1. Accédez à [!DNL samples/browserify/reference/build].
1. Exécutez les commandes suivantes :

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. Accédez à [!DNL samples/browserify/ui-framework/build].
1. Exécutez les mêmes commandes que celles de l’étape 2.

Une fois cette configuration terminée, vous pouvez créer des applications TVSDK compatibles avec les navigateurs en fonction des exemples fournis avec TVSDK.
