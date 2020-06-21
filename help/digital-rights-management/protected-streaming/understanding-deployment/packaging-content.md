---
description: Lorsque vous assemblez du contenu, vous devez spécifier l’URL du serveur de licences.
seo-description: Lorsque vous assemblez du contenu, vous devez spécifier l’URL du serveur de licences.
seo-title: Création d’un package de contenu
title: Création d’un package de contenu
uuid: 2e47a9a2-bbc6-4995-8ce5-6ca6b116349b
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Création d’un package de contenu{#packaging-content}

Lorsque vous assemblez du contenu, vous devez spécifier l’URL du serveur de licences.

L’URL du serveur DRM Adobe Primetime utilise le format suivant :

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

Par exemple, pour le nom d’hôte du serveur de licences `mylicenseserver.com` qui écoute sur le port 8080 et un locataire appelé *`tenant1`*, vous utiliseriez la syntaxe suivante pour l’URL du serveur de licences que vous spécifiez au moment où vous assemblez du contenu :

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Si chaque client utilise un serveur de licences et des informations d’identification de transport différents, veillez à spécifier le certificat du client approprié dans le gestionnaire de packages.

Si vous souhaitez vous assurer que le serveur ne délivre des licences qu’au contenu des packages connus, vous devez inclure le certificat de packager dans la liste autorisée packager du fichier de configuration du client.
