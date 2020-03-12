---
seo-title: Assemblage de contenu
title: Assemblage de contenu
uuid: 366c8470-b7ef-4a39-83c2-151ba9be9a32
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c

---


# Assemblage de contenu{#packaging-content}

Lorsque vous incluez du contenu pour des  de clés distantes, utilisez une stratégie qui spécifie que le de clés distantes est requis. L’URL du serveur de clés doit être incluse dans le fichier M3U8 (fichier manifeste) pour le contenu HLS. L’URL du serveur de clés DRM Primetime est au format suivant :

```
https://key-server-host:port/faxsks/tenant-name/key
```

Par exemple, pour le nom d’hôte du serveur de clé [!DNL mykeyserver.com] écoutant sur le port 443 et un client nommé `tenant1`, l’URL du serveur de clé à spécifier dans le M3U8 est :

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

La même URL peut être utilisée pour les clients iOS et Xbox 360. Ou, si le serveur est configuré avec des locataires distincts pour chaque type de client, différentes URL peuvent être utilisées.

Le même contenu peut être lu sur les clients qui ne nécessitent pas de serveur de clés, tant que l’URL du serveur de licences pointe vers un serveur de licences en cours d’exécution correctement configuré.
