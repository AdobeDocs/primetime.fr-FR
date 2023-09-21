---
description: Vous pouvez créer un lecteur compatible avec le navigateur à l’aide de fichiers JS fournis par le navigateur TVSDK.
title: Lecteur compatible avec la navigation
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Présentation {#browserify-compatible-player-overview}

Vous pouvez créer un lecteur compatible avec le navigateur à l’aide de fichiers JS fournis par le navigateur TVSDK.

Browser TVSDK fournit deux fichiers JS compatibles avec le navigateur. L’une d’elles est à utiliser avec le module AdobePSDK ; elle est destinée au développement d’applications sans interface utilisateur-framework. L’autre est à utiliser avec le module UI-Framework ; il renvoie l’espace de noms PTP que vous utilisez pour écrire des applications à l’aide de l’interface utilisateur-Framework.

Pour commencer à utiliser Browserify, exécutez les commandes de configuration suivantes pour créer [!DNL final.js] fichiers (votre fichier de bundle Browserify) dans la variable [!DNL example] répertoires sous [!DNL samples/browerify/reference] et [!DNL samples/browerify/ui-framework]:

1. Accédez à [!DNL samples/browserify/reference/build].
1. Exécutez les commandes suivantes :

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. Accédez à [!DNL samples/browserify/ui-framework/build].
1. Exécutez les mêmes commandes que dans l’étape 2.

Une fois cette configuration terminée, vous pouvez continuer à créer des applications TVSDK compatibles avec le navigateur en fonction des exemples fournis avec TVSDK.
