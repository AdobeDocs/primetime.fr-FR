---
title: Utilisation de l’implémentation de référence Primetime
description: Utilisation de l’implémentation de référence Primetime
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Utilisation de l’implémentation de référence Primetime {#how-to-use-the-primetime-reference-implementation}

L’implémentation de référence Primetime est un lecteur modulaire qui a été divisé en fonctionnalités individuelles que vous pouvez facilement modifier par le biais de gestionnaires de fonctionnalités spécialisés. Ces gestionnaires de fonctionnalités sont utilisés comme pont pour connecter l’application et la bibliothèque TVSDK.

Vous pouvez utiliser l’implémentation de référence comme suit :

* Utilisez-la en l’état sans modifier le code (toutes les fonctionnalités sont activées avec les valeurs par défaut).
* Utilisez-le comme référence pour comprendre comment utiliser la bibliothèque TVSDK.
* Choisissez les fonctionnalités qui s’appliquent à votre application en désactivant celles que vous n’utilisez pas.
* Personnalisez les composants de l’interface utilisateur sans apporter de modifications aux fonctionnalités.

Nous fournissons la mise en oeuvre de référence Primetime afin de vous aider à comprendre le TVSDK et à modifier facilement les gestionnaires de fonctionnalités pour personnaliser votre lecteur. Toutefois, reportez-vous au [Guide du programmeur Android TVSDK 1.4](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android.pdf) pour plus d’informations sur la bibliothèque TVSDK.

Pour accéder facilement à la documentation de l’API de mise en oeuvre de référence au format Javadoc, cliquez sur [here](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/index.html).
