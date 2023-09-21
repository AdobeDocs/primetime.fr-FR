---
title: Modules de contenu
description: Modules de contenu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Modules de contenu{#packaging-content}

Lors du conditionnement du contenu, l’URL du serveur de licences doit être spécifiée. L’URL Adobe Access Server est au format suivant :

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

Par exemple, pour le nom d’hôte du serveur de licences &quot;myconceserver.com&quot; qui écoute sur le port 8080 et un client nommé &quot;tenant1&quot;, l’URL du serveur de licences à spécifier au moment du conditionnement est :

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Si chaque client utilise un serveur de licences et des informations d’identification de transport différents, veillez à spécifier le certificat du client correct dans le programme de package.

Pour vous assurer que le serveur ne délivre des licences qu’au contenu conditionné par des modules connus, incluez le certificat du module dans la liste autorisée packager du fichier de configuration du client.
