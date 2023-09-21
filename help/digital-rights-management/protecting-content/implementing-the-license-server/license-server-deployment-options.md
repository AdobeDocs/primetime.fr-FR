---
title: Options de déploiement du serveur de licences
description: Options de déploiement du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Options de déploiement du serveur de licences{#license-server-deployment-options}

Vous pouvez déployer le serveur de licences à l’aide de l’une des options suivantes :

* Adobe Primetime DRM Server for Protected Streaming : ce serveur de licences est optimisé pour la diffusion en continu. Par exemple, vous pouvez configurer le serveur pour le HTTP Dynamic Streaming Adobe avec Primetime DRM. Ce serveur peut être déployé facilement avec très peu de configuration requise et prend en charge plusieurs clients. Il peut atteindre un haut niveau d’évolutivité. Cette implémentation étant optimisée pour la diffusion en continu, elle ne prend pas en charge les fonctionnalités complètes de Primetime DRM. Par exemple, l’authentification par nom d’utilisateur/mot de passe, les domaines et le chaînage de licences ne sont pas pris en charge. Les règles d’utilisation des licences délivrées par ce serveur sont contrôlées par un fichier de configuration de serveur, qui remplace la stratégie utilisée au moment du conditionnement.

  Voir *Guide de diffusion en continu protégée d’Adobe Primetime DRM Server* pour plus d’informations sur les règles d’utilisation prises en charge par le serveur de licences.
* Serveur de licences d’implémentation de référence : vous pouvez utiliser cette configuration pour personnaliser l’implémentation de votre serveur. Il s’agit d’un exemple de mise en oeuvre d’un serveur de licences, y compris le code source, qui montre comment utiliser les API du SDK DRM Primetime pour gérer tous les types de requêtes et comment implémenter une logique commerciale personnalisée basée sur une base de données. Les règles d’utilisation des licences délivrées par ce serveur sont contrôlées par la politique associée au contenu au moment du conditionnement.
* Mise en oeuvre personnalisée du serveur : vous pouvez également mettre en oeuvre votre propre serveur de licences avec le SDK. Ces informations décrivent comment les API sont utilisées pour mettre en oeuvre un serveur de licences.
