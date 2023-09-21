---
description: Lorsque vous mettez en package du contenu, vous devez spécifier l’URL du serveur de licences.
title: Modules de contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Modules de contenu{#packaging-content}

Lorsque vous mettez en package du contenu, vous devez spécifier l’URL du serveur de licences.

L’URL du serveur DRM Adobe Primetime utilise le format suivant :

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

Par exemple, pour le nom d’hôte du serveur de licences `mylicenseserver.com` qui écoute sur le port 8080, et un client appelé *`tenant1`*, vous utiliserez la syntaxe suivante pour l’URL du serveur de licences que vous spécifiez au moment où vous créez le package de contenu :

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Si chaque client utilise un serveur de licences et des informations d’identification de transport différents, veillez à spécifier le certificat du client correct dans le programme de package.

Si vous souhaitez vous assurer que le serveur n’accorde des licences qu’au contenu des modules connus, vous devez inclure le certificat du module dans la liste autorisée du module du fichier de configuration du client.
