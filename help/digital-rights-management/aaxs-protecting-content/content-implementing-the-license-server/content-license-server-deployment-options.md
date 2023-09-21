---
title: Options de déploiement du serveur de licences
description: Options de déploiement du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Options de déploiement du serveur de licences{#license-server-deployment-options}

Le serveur de licences peut être déployé à l’aide de l’une des options suivantes :

* **Adobe Access Server pour la diffusion en continu protégée** — Ce serveur de licences est optimisé pour la diffusion en continu. Par exemple, vous pouvez configurer le serveur pour le HTTP Dynamic Streaming Adobe avec accès Adobe. Ce serveur peut être déployé facilement avec très peu de configuration requise, il prend en charge plusieurs clients et peut atteindre un haut niveau d’évolutivité. Cependant, comme cette implémentation est optimisée pour la diffusion en continu, elle ne prend pas en charge les fonctionnalités d’accès complet aux Adobes. Par exemple, l’authentification par nom d’utilisateur/mot de passe, les domaines et le chaînage de licences ne sont pas pris en charge. Les règles d’utilisation des licences délivrées par ce serveur sont contrôlées par un fichier de configuration de serveur, qui remplace la stratégie utilisée au moment du conditionnement. Voir *Guide de diffusion en continu protégée d’Adobe Access Server* pour plus d’informations sur les règles d’utilisation prises en charge par ce serveur.
* **Serveur de licences d’implémentation de référence** — Utilisez cette configuration comme point de départ pour une mise en oeuvre de serveur personnalisée. Il s’agit d’un exemple de mise en oeuvre d’un serveur de licences, y compris le code source, qui montre comment utiliser les API du SDK Adobe Access pour gérer tous les types de requêtes et comment implémenter une logique commerciale personnalisée basée sur une base de données. Les règles d’utilisation des licences délivrées par ce serveur sont contrôlées par la politique associée au contenu au moment du conditionnement.
* **Mise en oeuvre personnalisée du serveur** — Vous pouvez également mettre en oeuvre votre propre serveur de licences à l’aide du SDK. Les informations de ce chapitre décrivent les API utilisées pour mettre en oeuvre un serveur de licences.
