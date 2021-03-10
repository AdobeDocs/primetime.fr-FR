---
description: Vous pouvez générer des jetons Expressplay pour leur contenu chiffré en envoyant des demandes de jeton au serveur de jetons Expressplay approprié.
title: Jetons Expressplay
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---


# Jetons Expressplay {#expressplay-tokens}

Vous pouvez générer des jetons Expressplay pour leur contenu chiffré en envoyant des demandes de jeton au serveur de jetons Expressplay approprié.

Voici un exemple :

```
https://wv-gen.service.expressplay.com/hms/wv/
token?customerAuthenticator=<your expressplay customer authenticator>
&kid=fd1a706ac2b36002888f6d4a414333c3
&contentKey=5438b719bf47a2f5678237477db2f9e6
&securityLevel=1
&hdcpOutputControl=0
```

L’ID d’enregistrement de clé de chiffrement de contenu ou le CEKSID attribué au paramètre `kid` et la clé de chiffrement de contenu ou le CEK attribué au paramètre `contentKey` doivent correspondre à l’ID d’enregistrement de clé de chiffrement de contenu et à la clé de chiffrement de contenu utilisés pour le pack. Le texte suivant est un exemple de réponse du serveur de jetons :

```
https://wv.service.expressplay.com/hms/wv/rights/
?ExpressPlayToken=AQAAABIDKbgAAABQbt68jktab0YRY-r9mo6VP
 VqDDvkHq78x4V9_AyBUTtcNFHw5JtNKlKrMt-4HBdJ3Fopr7fqFSBp
 SJ4o-d8teAkUZUtW3Od5V-SHsCLnAlbFW84K71h2xNUiMAvRcUFBG3bjxMQ
```

Vous pouvez alors

* utiliser l’URL et la requête renvoyées comme URL du serveur de licences, ou
* retirez la requête de l’URL et transmettez l’ExpressPlayToken séparément en tant qu’en-tête de POST HTTP.