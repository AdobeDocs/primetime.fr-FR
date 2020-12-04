---
seo-title: Chiffrement asymétrique des clés
title: Chiffrement asymétrique des clés
uuid: 0aae25f1-a609-4c73-9aef-13f8ae63f6e1
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Chiffrement asymétrique de la clé {#asymmetric-key-encryption}

Le chiffrement asymétrique des clés (également appelé chiffrement de clé publique) utilise des paires de clés. Une clé est utilisée pour le chiffrement ; l&#39;autre pour le déchiffrement. La clé de déchiffrement est gardée secrète et est appelée *clé privée*. La clé de chiffrement, appelée *clé publique*, est mise à la disposition de toute personne autorisée à chiffrer du contenu. Toute personne ayant accès à la clé publique peut chiffrer du contenu, mais seule une personne ayant accès à la clé privée peut le déchiffrer. La clé privée ne peut pas être reconstruite à partir de la clé publique.

Lors de l’assemblage de contenu, la clé publique du serveur de licences est utilisée pour chiffrer la clé de chiffrement de contenu (CEK) dans les métadonnées DRM. Vous devez vous assurer que seul le serveur de licences a accès à la clé privée du serveur de licences ; si quelqu&#39;un d&#39;autre a la clé, il peut déchiffrer et vue le contenu.

***Attention :**Assurez-vous d&#39;obtenir le certificat du serveur de licences (contenant la clé publique) auprès d&#39;une source approuvée afin de vous assurer qu&#39;il s&#39;agit de la clé du serveur de licences et non d&#39;une clé publique non fiable. Si un attaquant devait remplacer la clé du serveur de licences par sa clé publique, il serait en mesure de déchiffrer votre contenu.*

Pour plus d’informations sur l’emballage du contenu, voir *Utilisation du SDK Adobe Access pour la protection du contenu*.
