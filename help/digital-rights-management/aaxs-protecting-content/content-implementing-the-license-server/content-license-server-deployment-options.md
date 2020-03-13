---
seo-title: Options de déploiement du serveur de licences
title: Options de déploiement du serveur de licences
uuid: 297c587f-23e2-4bb5-911b-72d7b82370f4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Options de déploiement du serveur de licences{#license-server-deployment-options}

Le serveur de licences peut être déployé à l’aide de l’une des options suivantes :

* **Adobe Access Server for Protected Streaming** — Ce serveur de licence est optimisé pour la diffusion en flux continu. Par exemple, vous pouvez configurer le serveur pour Adobe HTTP Dynamic Streaming avec Adobe Access. Ce serveur peut être déployé facilement avec très peu de configuration requise et prendra en charge plusieurs locataires, et peut atteindre un haut niveau d&#39;évolutivité. Toutefois, cette implémentation étant optimisée pour la diffusion en flux continu, elle ne prend pas en charge l’ensemble des fonctionnalités d’Adobe Access. Par exemple, l’authentification par nom d’utilisateur/mot de passe, les domaines et le chaînage de licences ne sont pas pris en charge. Les règles d’utilisation des licences émises par ce serveur sont contrôlées par le biais d’un fichier de configuration de serveur, qui remplace la stratégie utilisée au moment de la création du pack. Pour plus d’informations sur les règles d’utilisation prises en charge par ce serveur, reportez-vous au Guide *de diffusion en flux continu protégée d’* Adobe Access Server for Protected Streaming.
* **Serveur** de licence d&#39;implémentation de référence : utilisez cette configuration comme point de départ pour une implémentation de serveur personnalisé. Il s’agit d’un exemple de mise en oeuvre du serveur de licences, y compris le code source, qui montre comment utiliser les API du SDK Adobe Access pour traiter tous les types de requêtes et comment implémenter une logique métier personnalisée avec l’aide d’une base de données. Les règles d’utilisation des licences émises par ce serveur sont contrôlées par le biais de la stratégie associée au contenu au moment de la création du pack.
* **Implémentation** de serveur personnalisé : vous pouvez également mettre en oeuvre votre propre serveur de licences à l’aide du SDK. Les informations de ce chapitre décrivent les API utilisées pour implémenter un serveur de licences.

