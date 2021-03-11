---
title: Diffusion de clés iOS distante et locale
description: Diffusion de clés iOS distante et locale
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Diffusion de clés iOS distante et locale {#remote-and-local-ios-key-delivery}

Adobe Primetime prend en charge les options suivantes pour les diffusions clés aux clients iOS :

* **Remote**  - Effectue les opérations conformément aux spécifications HLS (HTTP Live Streaming) ; le manifeste M3U8 spécifie un chemin HTTPS qui inclut une clé AES qui doit être utilisée pour déchiffrer les segments chiffrés suivants dans le flux. Lorsque vous spécifiez `Remote` dans la stratégie DRM Primetime, le périphérique client doit se connecter à un serveur HTTPS distant pour obtenir une clé AES.

* **Local**  - Lorsque vous spécifiez  `Local` dans le DRM Primetime au lieu de vous connecter à Internet/réseau pour la clé AES, un serveur HTTPS local est incorporé à l&#39;application iOS, qui gère ensuite toutes les requêtes clés AES. Le serveur HTTPS incorporé est automatiquement configuré et configuré dans l’application P. Aucune intervention n’est requise de la part du développeur d’applications.

La diffusion des clés distantes est activée par le biais de la stratégie DRM Primetime utilisée pour compresser le contenu. Si vous souhaitez modifier ce paramètre, vous devez recompresser le contenu. Si vous activez la diffusion de clés distantes, vous devez déployer un serveur de clés DRM Primetime capable de gérer les requêtes clés des clients iOS. Toutefois, le flux de travail des clients sur d’autres plateformes n’a pas été modifié.

>[!NOTE]
>
>La sélection de la diffusion clé n’affecte que les clients iOS. Tous les autres périphériques qui utilisent le contenu HLS, tels que Android et Primetime sur le bureau (Flash Player), utilisent toujours la diffusion de clé `Local`, même si `Remote` a été spécifié.

