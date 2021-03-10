---
description: Vous pouvez créer un lecteur compatible avec le navigateur à l’aide de fichiers JS fournis par le navigateur TVSDK.
title: Lecteur compatible avec la navigation
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Aperçu {#browserify-compatible-player-overview}

Vous pouvez créer un lecteur compatible avec le navigateur à l’aide de fichiers JS fournis par le navigateur TVSDK.

Le navigateur TVSDK fournit deux fichiers JS compatibles avec le navigateur. L’un est destiné au module AdobePSDK ; il s’agit du développement d’applications sans interface utilisateur-Framework. L&#39;autre est destiné au module UI-Framework ; il renvoie l’espace de nommage PTP que vous utilisez pour écrire des applications à l’aide de UI-Framework.

Pour commencer à utiliser Browserify, exécutez les commandes de configuration suivantes pour créer des fichiers [!DNL final.js] (votre fichier d&#39;assemblage Browserify) dans les répertoires [!DNL example] situés sous [!DNL samples/browerify/reference] et [!DNL samples/browerify/ui-framework] :

1. Accédez à [!DNL samples/browserify/reference/build].
1. Exécutez les commandes suivantes :

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. Accédez à [!DNL samples/browserify/ui-framework/build].
1. Exécutez les mêmes commandes que celles de l’étape 2.

Une fois cette configuration terminée, vous pouvez continuer à créer des applications TVSDK compatibles avec les navigateurs en vous basant sur les exemples fournis avec TVSDK.
