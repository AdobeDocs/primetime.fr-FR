---
title: Options de déploiement du serveur de licences
description: Options de déploiement du serveur de licences
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---


# Options de déploiement du serveur de licences{#license-server-deployment-options}

Le serveur de licences peut être déployé à l’aide de l’une des options suivantes :

* **Adobe Access Server for Protected Streaming**  (pour la diffusion en flux continuprotégée) : ce serveur de licence est optimisé pour la diffusion en flux continu. Par exemple, vous pouvez configurer le serveur pour un HTTP Dynamic Streaming d’Adobe avec Adobe Access. Ce serveur peut être déployé facilement avec très peu de configuration requise et prendra en charge plusieurs locataires, et peut atteindre un haut niveau d&#39;évolutivité. Cependant, comme cette implémentation est optimisée pour la diffusion en flux continu, elle ne prend pas en charge les fonctionnalités d’accès à l’Adobe complet. Par exemple, l’authentification par nom d’utilisateur/mot de passe, les domaines et le chaînage de licences ne sont pas pris en charge. Les règles d’utilisation des licences délivrées par ce serveur sont contrôlées par le biais d’un fichier de configuration de serveur, qui remplace la stratégie utilisée au moment du conditionnement. Pour plus d&#39;informations sur les règles d&#39;utilisation prises en charge par ce serveur, consultez le *Guide de diffusion en flux continu protégé de l&#39;Adobe Access Server*.
* **Serveur**  de licence d&#39;implémentation de référence : utilisez cette configuration comme point de départ pour une implémentation de serveur personnalisé. Il s’agit d’un exemple de mise en oeuvre du serveur de licences, y compris le code source, qui montre comment utiliser les API du SDK Adobe Access pour gérer tous les types de requêtes et comment implémenter une logique métier personnalisée soutenue par une base de données. Les règles d’utilisation des licences délivrées par ce serveur sont contrôlées par la stratégie associée au contenu au moment de l’assemblage.
* **Implémentation**  de serveur personnalisé : vous pouvez également mettre en oeuvre votre propre serveur de licences à l’aide du SDK. Les informations de ce chapitre décrivent les API utilisées pour implémenter un serveur de licences.

