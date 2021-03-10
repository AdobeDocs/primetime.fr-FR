---
title: Vérifier la compatibilité avec Flash Media Rights Management Server 1.x
description: Vérifier la compatibilité avec Flash Media Rights Management Server 1.x
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Vérifier la compatibilité avec Flash Media Rights Management Server 1.x{#ensure-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.x et Adobe Access utilisent des métadonnées différentes pour le conditionnement du contenu et la demande de licences. Pour que l’accès à l’Adobe utilise le contenu FMRMS version 1.x, les métadonnées doivent être converties.

Le SDK Adobe Access prend en charge deux options de conversion des métadonnées :

* Hors ligne (recommandé)

   Générez les métadonnées Accès à l’Adobe dans un processus hors ligne et stockez-les pour les utiliser lorsqu’un client les demande. L’Adobe recommande cette option. Si les métadonnées sont générées hors connexion, le serveur de licences n’a pas besoin d’accéder aux CEK 1.x ni aux informations d’identification de l’outil de création de package. En outre, la conversion des offres hors ligne améliore les performances car le serveur de licences n’a pas besoin de générer les métadonnées en temps réel.

* À la demande

   Générez à la demande les métadonnées d’accès à l’Adobe lorsqu’un client le demande. Lorsqu&#39;un client Adobe Access télécharge le contenu de la version 1.x, il envoie les métadonnées DRM (également connues sous le nom d&#39;en-tête DRM) au SDK Adobe Access. Le SDK convertit les métadonnées DRM au format actuel. Le SDK chiffre et incorpore la clé de chiffrement de contenu (CEK) dans les métadonnées et renvoie le contenu au client Adobe Access. (Les métadonnées Adobe Access 1.x ne contiennent pas le CEK.)

   Pour convertir les métadonnées, Accès aux Adobes nécessite l&#39;accès aux clés de chiffrement de contenu Adobe Access 1.x. Lorsque vous effectuez une migration depuis Flash Media Rights Management Server 1.x, vous pouvez continuer à stocker les clés de chiffrement de contenu dans la base de données LiveCycle ES ou vous pouvez mettre en oeuvre une solution personnalisée pour stocker en toute sécurité les clés de chiffrement de contenu ailleurs. Si vous choisissez de continuer à stocker les clés de chiffrement de contenu dans la base de données de LiveCycle ES, suivez les recommandations de la section &quot;Protection de l&#39;accès au contenu sensible dans la base de données&quot; dans *Renforcement et sécurité du LiveCycle ES*.

Pour plus d’informations sur la compatibilité avec le contenu compressé à l’aide de Flash Media Rights Management Server 1.x, voir *Adobe Access API Reference*.
