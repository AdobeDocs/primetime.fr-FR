---
description: Vous pouvez générer des jetons Expressplay pour leur contenu chiffré en envoyant des demandes de jeton au serveur de jetons Expressplay approprié.
seo-description: Vous pouvez générer des jetons Expressplay pour leur contenu chiffré en envoyant des demandes de jeton au serveur de jetons Expressplay approprié.
seo-title: Jetons Expressplay
title: Jetons Expressplay
uuid: 6103e1b2-127d-4758-a589-15f0f3c73db1
translation-type: tm+mt
source-git-commit: d0ba1f98b16f6350ae842ca2ce1261bf49dd8a66

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

L’ID d’enregistrement de la clé de chiffrement de contenu ou le CEKSID attribué au `kid` paramètre et la clé de chiffrement de contenu ou le CEK attribué au `contentKey` paramètre doivent correspondre à l’ID d’enregistrement de la clé de chiffrement de contenu et à la clé de chiffrement de contenu utilisée pour le conditionnement. Le texte suivant est un exemple de réponse du serveur de jetons :

```
https://wv.service.expressplay.com/hms/wv/rights/
?ExpressPlayToken=AQAAABIDKbgAAABQbt68jktab0YRY-r9mo6VP
 VqDDvkHq78x4V9_AyBUTtcNFHw5JtNKlKrMt-4HBdJ3Fopr7fqFSBp
 SJ4o-d8teAkUZUtW3Od5V-SHsCLnAlbFW84K71h2xNUiMAvRcUFBG3bjxMQ
```

Vous pouvez alors

* utiliser l’URL et la requête renvoyées comme URL du serveur de licences, ou
* retirez la requête de l’URL et transmettez l’ExpressPlayToken séparément sous forme d’en-tête HTTP POST.