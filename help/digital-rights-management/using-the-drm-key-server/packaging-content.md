---
seo-title: Création d’un package de contenu
title: Création d’un package de contenu
uuid: 366c8470-b7ef-4a39-83c2-151ba9be9a32
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Création d’un package de contenu {#packaging-content}

Lorsque vous incluez du contenu pour la diffusion de clés distantes, utilisez une stratégie qui spécifie que la diffusion de clés distantes est requise. L&#39;URL du serveur de clés doit être incluse dans le fichier de manifeste M3U8 pour le contenu HLS. L&#39;URL du serveur clé DRM de Primetime est au format suivant :

```
https://key-server-host:port/faxsks/tenant-name/key
```

Par exemple, pour le nom d’hôte du serveur de clés [!DNL mykeyserver.com] qui écoute sur le port 443 et un client nommé `tenant1`, l’URL de serveur de clés à spécifier dans le M3U8 est :

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

La même URL peut être utilisée pour les clients iOS et Xbox 360. Ou, si le serveur est configuré avec des locataires distincts pour chaque type de client, différentes URL peuvent être utilisées.

Le même contenu peut être lu sur les clients qui n’ont pas besoin d’un serveur clé, tant que l’URL du serveur de licences pointe vers un serveur de licences en cours d’exécution correctement configuré.
