---
seo-title: Création d’un package de contenu
title: Création d’un package de contenu
uuid: 5d1d4b9d-f241-4291-9577-e9de5a8b92be
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

---


# Création d’un package de contenu{#packaging-content}

Lors de la création d’un pack de contenu, l’URL du serveur de licences doit être spécifiée. L’URL du serveur Adobe Access a le format suivant :

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

Par exemple, pour le nom d’hôte du serveur de licences &quot;myconceserver.com&quot; qui écoute sur le port 8080 et un client nommé &quot;client1&quot;, l’URL du serveur de licences à spécifier au moment du conditionnement est :

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Si chaque client utilise un serveur de licences et des informations d’identification de transport différents, veillez à spécifier le certificat du client approprié dans le gestionnaire de packages.

Pour s’assurer que le serveur ne délivre des licences qu’au contenu conditionné par des packagers connus, incluez le certificat du packager dans la liste blanche de packager du fichier de configuration du locataire.
