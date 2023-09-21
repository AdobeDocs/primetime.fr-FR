---
title: Diffusion clé iOS locale et distante
description: Diffusion clé iOS locale et distante
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Diffusion clé iOS locale et distante {#remote-and-local-ios-key-delivery}

Adobe Primetime prend en charge les options suivantes pour la diffusion clé vers les clients iOS :

* **Distant** : s’exécute comme spécifié dans la spécification HTTP Live Streaming (HLS) ; le manifeste M3U8 spécifie un chemin HTTPS qui inclut une clé AES à utiliser pour déchiffrer les segments chiffrés suivants dans le flux. Lorsque vous spécifiez `Remote` dans la stratégie DRM Primetime, le périphérique client doit se connecter à un serveur HTTPS distant pour obtenir une clé AES.

* **Local** - Lorsque vous spécifiez `Local` dans Primetime DRM, au lieu de se connecter à Internet/réseau pour la clé AES, un serveur HTTPS local est intégré à l’application iOS, qui gère ensuite toutes les demandes clés AES. Le serveur HTTPS incorporé est automatiquement configuré et configuré dans l’application P. Aucune intervention n’est requise par le développeur de l’application.

La diffusion de clé distante est activée par le biais de la stratégie DRM Primetime utilisée pour empaqueter le contenu. Si vous souhaitez modifier ce paramètre, vous devez recompresser le contenu. Si vous activez la diffusion à distance par clé, vous devez déployer un serveur de clés DRM Primetime capable de gérer les demandes clés des clients iOS. Toutefois, le workflow des clients sur d’autres plateformes n’a pas été modifié.

>[!NOTE]
>
>La sélection de diffusion Clé n’affecte que les clients iOS. Tous les autres appareils qui utilisent du contenu HLS , comme Android et Primetime on Desktop (par Flash Player), utilisent toujours `Local` diffusion clé, même si `Remote` a été spécifié.
