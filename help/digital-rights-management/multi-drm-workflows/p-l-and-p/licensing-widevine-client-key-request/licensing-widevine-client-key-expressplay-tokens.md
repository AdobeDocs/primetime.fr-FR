---
description: Vous pouvez générer des jetons Expressplay pour leur contenu chiffré en envoyant des requêtes de jeton au serveur de jeton Expressplay approprié.
title: Jetons Expressplay
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Jetons Expressplay {#expressplay-tokens}

Vous pouvez générer des jetons Expressplay pour leur contenu chiffré en envoyant des requêtes de jeton au serveur de jeton Expressplay approprié.

Voici un exemple d’URL :

```
https://wv-gen.service.expressplay.com/hms/wv/
token?customerAuthenticator=<your expressplay customer authenticator>
&kid=fd1a706ac2b36002888f6d4a414333c3
&contentKey=5438b719bf47a2f5678237477db2f9e6
&securityLevel=1
&hdcpOutputControl=0
```

ID de stockage de la clé de chiffrement du contenu ou CEKSID attribué à la variable `kid` et la clé de chiffrement du contenu ou le CEK attribué à la variable `contentKey` doit correspondre à l’ID de stockage de la clé de chiffrement du contenu et à la clé de chiffrement du contenu utilisés pour le package. Le texte suivant est un exemple de réponse du serveur de jetons :

```
https://wv.service.expressplay.com/hms/wv/rights/
?ExpressPlayToken=AQAAABIDKbgAAABQbt68jktab0YRY-r9mo6VP
 VqDDvkHq78x4V9_AyBUTtcNFHw5JtNKlKrMt-4HBdJ3Fopr7fqFSBp
 SJ4o-d8teAkUZUtW3Od5V-SHsCLnAlbFW84K71h2xNUiMAvRcUFBG3bjxMQ
```

Vous pouvez alors :

* utiliser l’URL et la requête renvoyées comme URL du serveur de licences, ou
* Supprimez la requête de l’URL et transmettez séparément le jeton ExpressPlayToken en tant qu’en-tête de POST HTTP.
