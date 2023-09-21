---
title: Modules de contenu
description: Modules de contenu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Modules de contenu{#packaging-content}

Lors du conditionnement du contenu pour une diffusion à clé distante, utilisez une stratégie qui spécifie que la diffusion à clé distante est requise. L’URL du serveur de clés doit être incluse dans le fichier de manifeste M3U8 pour le contenu HLS. L’URL Primetime DRM Key Server a le format suivant :

```
https://key-server-host:port/faxsks/tenant-name/key
```

Par exemple, pour le nom d’hôte du serveur de clés [!DNL mykeyserver.com] écoute sur le port 443 et un client nommé `tenant1`, l’URL du serveur clé à spécifier dans le M3U8 est :

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

La même URL peut être utilisée pour les clients iOS et Xbox 360. Ou, si le serveur est configuré avec des clients distincts pour chaque type de client, différentes URL peuvent être utilisées.

Le même contenu peut être lu sur les clients qui ne nécessitent pas de serveur clé, à condition que l’URL du serveur de licences pointe vers un serveur de licences d’exécution correctement configuré.
