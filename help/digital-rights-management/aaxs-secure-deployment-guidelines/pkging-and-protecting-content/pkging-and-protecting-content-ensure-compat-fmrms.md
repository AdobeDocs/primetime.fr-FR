---
title: Vérifier la compatibilité avec Flash Media Rights Management Server 1.x
description: Vérifier la compatibilité avec Flash Media Rights Management Server 1.x
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Vérifier la compatibilité avec Flash Media Rights Management Server 1.x{#ensure-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.x et Adobe Access utilisent différentes métadonnées pour empaqueter le contenu et demander des licences. Pour que Adobe Access utilise le contenu FMRMS version 1.x, les métadonnées doivent être converties.

Le SDK Adobe Access prend en charge deux options de conversion des métadonnées :

* Hors ligne (recommandé)

  Générez les métadonnées Accès à l’Adobe dans un processus hors ligne et stockez-les pour les utiliser lorsqu’un client les demande. Adobe recommande cette option. Si les métadonnées sont générées hors ligne, le serveur de licences n’a pas besoin d’accéder aux CEK 1.x ni aux informations d’identification de packager. En outre, la conversion hors ligne offre de meilleures performances car le serveur de licences n’a pas besoin de générer les métadonnées en temps réel.

* À la demande

  Générez les métadonnées Accès à l’Adobe à la demande lorsqu’un client le demande. Lorsqu’un client Adobe Access télécharge le contenu de la version 1.x, il envoie les métadonnées DRM (également appelées en-tête DRM) au SDK Adobe Access. Le SDK convertit les métadonnées DRM au format actuel. Le SDK chiffre et incorpore la clé de chiffrement de contenu (CEK) dans les métadonnées et renvoie le contenu au client Adobe Access. (Les métadonnées Adobe Access 1.x ne contiennent pas le CEK.)

  Pour convertir les métadonnées, Adobe Access nécessite l’accès aux clés de chiffrement de contenu Adobe Access 1.x. Lorsque vous migrez depuis Flash Media Rights Management Server 1.x, vous pouvez continuer à stocker les clés de chiffrement de contenu dans la base de données LiveCycle ES, ou vous pouvez mettre en oeuvre une solution personnalisée pour stocker les clés de chiffrement de contenu en toute sécurité ailleurs. Si vous choisissez de continuer à stocker les clés de chiffrement de contenu dans la base de données LiveCycle ES, suivez les recommandations décrites dans la section &quot;Protection de l’accès aux contenus sensibles dans la base de données&quot; dans *Renforcement et sécurité du LiveCycle ES*.

Pour plus d’informations sur la compatibilité avec le contenu empaqueté à l’aide de Flash Media Rights Management Server 1.x, voir *Référence de l’API Adobe Access*.
