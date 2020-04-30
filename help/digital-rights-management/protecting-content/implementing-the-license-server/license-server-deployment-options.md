---
seo-title: Options de déploiement du serveur de licences
title: Options de déploiement du serveur de licences
uuid: 732b948f-8037-423e-9f85-770d6316cbae
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Options de déploiement du serveur de licences{#license-server-deployment-options}

Vous pouvez déployer le serveur de licences en utilisant l’une des options suivantes :

* Adobe Primetime DRM Server for Protected Streaming : ce serveur de licence est optimisé pour la diffusion en flux continu. Par exemple, vous pouvez configurer le serveur pour la diffusion en flux continu dynamique HTTP Adobe avec Primetime DRM. Ce serveur peut être déployé facilement avec très peu de configuration requise et prend en charge plusieurs locataires. Il peut atteindre un haut niveau d&#39;évolutivité. Cette mise en oeuvre étant optimisée pour la diffusion en continu, elle ne prend pas en charge l’ensemble des fonctionnalités DRM Primetime. Par exemple, l’authentification par nom d’utilisateur/mot de passe, les domaines et le chaînage de licences ne sont pas pris en charge. Les règles d’utilisation des licences délivrées par ce serveur sont contrôlées par le biais d’un fichier de configuration de serveur, qui remplace la stratégie utilisée au moment du conditionnement.

   Pour plus d’informations sur les règles d’utilisation prises en charge par le serveur de licence, consultez le Guide *de diffusion en continu protégée d’* Adobe Primetime DRM Server for Protected Streaming.
* Serveur de licences d&#39;implémentation de référence : vous pouvez utiliser cette configuration pour personnaliser l&#39;implémentation de votre serveur. Il s’agit d’un exemple de mise en oeuvre du serveur de licences, y compris le code source, qui montre comment utiliser les API du SDK DRM de Primetime pour gérer tous les types de requêtes et comment implémenter une logique métier personnalisée soutenue par une base de données. Les règles d’utilisation des licences délivrées par ce serveur sont contrôlées par la stratégie associée au contenu au moment de l’assemblage.
* Implémentation de serveur personnalisé : vous pouvez également mettre en oeuvre votre propre serveur de licences avec le SDK. Ces informations décrivent comment les API sont utilisées pour implémenter un serveur de licences.

