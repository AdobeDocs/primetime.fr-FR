---
title: Création d’un package de contenu
description: Création d’un package de contenu
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Création d’un package de contenu {#packaging-content}

Lors de la création d’un pack de contenu, l’URL du serveur de licences doit être spécifiée. L’URL Adobe Access Server est au format suivant :

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

Par exemple, pour le nom d’hôte du serveur de licences &quot;myconceserver.com&quot; qui écoute sur le port 8080 et un client nommé &quot;client1&quot;, l’URL du serveur de licences à spécifier au moment du conditionnement est :

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Si chaque client utilise un serveur de licences et des informations d’identification de transport différents, veillez à spécifier le certificat du client approprié dans le gestionnaire de packages.

Pour s’assurer que le serveur ne délivre des licences qu’au contenu conditionné par des packages connus, incluez le certificat de packager dans la liste autorisée packager du fichier de configuration du client.
