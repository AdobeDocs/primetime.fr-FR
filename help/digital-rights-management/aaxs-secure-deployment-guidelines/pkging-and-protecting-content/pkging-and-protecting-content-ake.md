---
title: Cryptage de clé asymétrique
description: Cryptage de clé asymétrique
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Cryptage de clé asymétrique{#asymmetric-key-encryption}

Le cryptage de clé asymétrique (également appelé cryptage de clé publique) utilise des paires de clés. Une clé est utilisée pour le cryptage, l’autre pour le décryptage. La clé de décryptage est tenue secrète et est appelée *clé privée*. La clé de chiffrement, appelée *clé publique*, est mis à la disposition de toute personne autorisée à chiffrer du contenu. Toute personne ayant accès à la clé publique peut chiffrer du contenu, mais seule une personne ayant accès à la clé privée peut le déchiffrer. La clé privée ne peut pas être reconstruite à partir de la clé publique.

Lors du regroupement de contenu, la clé publique du serveur de licences est utilisée pour chiffrer la clé de chiffrement de contenu (CEK) dans les métadonnées DRM. Vous devez vous assurer que seul le serveur de licences a accès à la clé privée du serveur de licences ; si quelqu’un d’autre dispose de la clé, il peut la déchiffrer et afficher le contenu.

***Attention :**Assurez-vous d’obtenir le certificat du serveur de licences (contenant la clé publique) d’une source de confiance afin que vous puissiez être certain qu’il s’agit de la clé du serveur de licences et non d’une clé publique non fiable. Si un attaquant devait substituer sa clé publique à la clé du serveur de licences, il serait en mesure de déchiffrer votre contenu.*

Pour plus d’informations sur le contenu du package, voir *Utilisation du SDK Adobe Access pour la protection du contenu*.
