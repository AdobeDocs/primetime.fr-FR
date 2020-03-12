---
seo-title: Options de déploiement du serveur de licences
title: Options de déploiement du serveur de licences
uuid: 732b948f-8037-423e-9f85-770d6316cbae
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Options de déploiement du serveur de licences{#license-server-deployment-options}

Vous pouvez déployer le serveur de licences à l’aide de l’une des options suivantes :

* Serveur DRM Adobe Primetime pour la diffusion en flux continu protégée : ce serveur de licence est optimisé pour la diffusion en flux continu. Par exemple, vous pouvez configurer le serveur pour Adobe HTTP Dynamic Streaming avec Primetime DRM. Ce serveur peut être déployé facilement avec très peu de configuration requise et prend en charge plusieurs locataires. Il peut atteindre un haut niveau d&#39;évolutivité. Cette implémentation étant optimisée pour la diffusion en flux continu, elle ne prend pas en charge les fonctionnalités DRM Primetime complètes. Par exemple, l’authentification par nom d’utilisateur/mot de passe, les domaines et le chaînage de licences ne sont pas pris en charge. Les règles d’utilisation des licences émises par ce serveur sont contrôlées par le biais d’un fichier de configuration de serveur, qui remplace la stratégie utilisée au moment de la création du pack.

   Pour plus d’informations sur les règles d’utilisation prises en charge par le serveur de licence, reportez-vous au Guide *de diffusion en continu protégée d’* Adobe Primetime DRM Server for Protected Streaming.
* Serveur de licences d&#39;implémentation de référence : vous pouvez utiliser cette configuration pour personnaliser l&#39;implémentation de votre serveur. Il s’agit d’un exemple d’implémentation du serveur de licences, y compris le code source, qui montre comment utiliser les API du SDK DRM Primetime pour gérer tous les types de requêtes et comment implémenter une logique métier personnalisée avec l’aide d’une base de données. Les règles d’utilisation des licences émises par ce serveur sont contrôlées par le biais de la stratégie associée au contenu au moment de la création du pack.
* Implémentation de serveur personnalisé : vous pouvez également mettre en oeuvre votre propre serveur de licences avec le SDK. Ces informations décrivent comment les API sont utilisées pour implémenter un serveur de licences.

