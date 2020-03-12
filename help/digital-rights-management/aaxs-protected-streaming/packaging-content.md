---
seo-title: Assemblage de contenu
title: Assemblage de contenu
uuid: 5d1d4b9d-f241-4291-9577-e9de5a8b92be
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

---


# Assemblage de contenu{#packaging-content}

Lors de l’assemblage du contenu, l’URL du serveur de licences doit être spécifiée. L’URL du serveur Adobe Access a le format suivant :

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

Par exemple, pour le nom d’hôte du serveur de licences &quot;myconceserver.com&quot; qui écoute sur le port 8080 et un client nommé &quot;client1&quot;, l’URL du serveur de licences à spécifier au moment du conditionnement est :

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Si chaque client utilise un serveur de licences et des informations d’identification de transport différents, veillez à spécifier le certificat du client correct dans le gestionnaire de package.

Pour vous assurer que le serveur ne délivre des licences qu’au contenu compressé par des gestionnaires de package connus, incluez le certificat du gestionnaire de package dans la liste blanche du fichier de configuration du client.
