---
seo-title: 'clé iOS local et distant '
title: 'clé iOS local et distant '
uuid: 90f672e7-9301-4e14-adca-db2a8f951a83
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# clé iOS local et distant {#remote-and-local-ios-key-delivery}

Adobe Primetime prend en charge les options suivantes pour les  clés aux clients iOS :

* **Remote** - Effectue comme spécifié dans la spécification HTTP Live Streaming (HLS) ; le manifeste M3U8 spécifie un chemin HTTPS incluant une clé AES qui doit être utilisée pour déchiffrer les segments chiffrés suivants dans le flux. Lorsque vous spécifiez `Remote` dans la stratégie DRM Primetime, le périphérique client doit se connecter à un serveur HTTPS distant pour obtenir une clé AES.

* **Local** - Lorsque vous spécifiez `Local` dans le DRM Primetime au lieu de vous connecter à Internet/réseau pour la clé AES, un serveur HTTPS local est intégré dans l’application iOS, qui gère ensuite toutes les requêtes de clés AES. Le serveur HTTPS intégré est automatiquement configuré et configuré dans l’application P. Aucune intervention n’est requise de la part du développeur d’applications.

Le de clés distantes est activé via la stratégie DRM Primetime utilisée pour compresser le contenu. Si vous souhaitez modifier ce paramètre, vous devez recompresser le contenu. Si vous activez les  de clés distantes, vous devez déployer un serveur de clés DRM Primetime capable de gérer les demandes de clés des clients iOS. Toutefois, le flux de travail des clients sur d’autres plateformes n’est pas modifié.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>La sélection des  clés n’affecte que les clients iOS. Tous les autres périphériques qui utilisent du contenu HLS, tels que Android et Primetime on Desktop (Flash Player), utilisent toujours des  de `Local` clés, même `Remote` si cela a été spécifié.

