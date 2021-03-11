---
description: Lorsque vous assemblez du contenu, vous devez spécifier l’URL du serveur de licences.
title: Création d’un package de contenu
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# Création d’un package de contenu {#packaging-content}

Lorsque vous assemblez du contenu, vous devez spécifier l’URL du serveur de licences.

L’URL du serveur DRM Adobe Primetime utilise le format suivant :

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

Par exemple, pour le nom d’hôte du serveur de licences `mylicenseserver.com` qui écoute sur le port 8080 et un client appelé *`tenant1`*, vous utiliseriez la syntaxe suivante pour l’URL du serveur de licences que vous spécifiez au moment où vous incluez le contenu du package :

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Si chaque client utilise un serveur de licences et des informations d’identification de transport différents, veillez à spécifier le certificat du client approprié dans le gestionnaire de packages.

Si vous souhaitez vous assurer que le serveur ne délivre des licences qu’au contenu des packages connus, vous devez inclure le certificat de packager dans la liste autorisée packager du fichier de configuration du client.
