---
seo-title: diffusion de clés iOS distante et locale
title: diffusion de clés iOS distante et locale
uuid: 90f672e7-9301-4e14-adca-db2a8f951a83
translation-type: tm+mt
source-git-commit: ''

---


# diffusion de clés iOS distante et locale {#remote-and-local-ios-key-delivery}

Adobe Primetime prend en charge les options suivantes pour les diffusions clés aux clients iOS :

* **Remote** - Effectue comme spécifié dans la spécification HTTP Live Streaming (HLS) ; le manifeste M3U8 spécifie un chemin HTTPS qui inclut une clé AES qui doit être utilisée pour déchiffrer les segments chiffrés suivants dans le flux. Lorsque vous spécifiez `Remote` dans la stratégie DRM Primetime, le périphérique client doit se connecter à un serveur HTTPS distant pour obtenir une clé AES.

* **Local** - Lorsque vous spécifiez `Local` dans le DRM Primetime au lieu de vous connecter à Internet/réseau pour la clé AES, un serveur HTTPS local est incorporé à l’application iOS, qui gère ensuite toutes les requêtes clés AES. Le serveur HTTPS incorporé est automatiquement configuré et configuré dans l’application P. Aucune intervention n’est requise de la part du développeur d’applications.

La diffusion des clés distantes est activée par le biais de la stratégie DRM Primetime utilisée pour compresser le contenu. Si vous souhaitez modifier ce paramètre, vous devez recompresser le contenu. Si vous activez la diffusion de clés distantes, vous devez déployer un serveur de clés DRM Primetime capable de gérer les requêtes clés des clients iOS. Toutefois, le flux de travail des clients sur d’autres plateformes n’a pas été modifié.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>La sélection de la diffusion clé n’affecte que les clients iOS. Tous les autres périphériques qui utilisent du contenu HLS, tels que Android et Primetime sur le bureau (Flash Player), utilisent toujours `Local` la diffusion clé, même si `Remote` cela a été spécifié.

