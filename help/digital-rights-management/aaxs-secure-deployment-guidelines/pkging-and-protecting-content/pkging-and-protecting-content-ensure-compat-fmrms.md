---
seo-title: Vérifier la compatibilité avec Flash Media Rights Management Server 1.x
title: Vérifier la compatibilité avec Flash Media Rights Management Server 1.x
uuid: 0160ca02-ebe6-4090-bf32-1d1a46088844
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Vérifier la compatibilité avec Flash Media Rights Management Server 1.x{#ensure-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.x et Adobe Access utilisent des métadonnées différentes pour créer un pack de contenu et demander des licences. Pour qu’Adobe Access utilise le contenu FMRMS version 1.x, les métadonnées doivent être converties.

Le SDK Adobe Access prend en charge deux options de conversion des métadonnées :

* Hors ligne (recommandé)

   Générez les métadonnées Adobe Access dans un processus hors ligne et stockez-les pour les utiliser lorsqu’un client les demande. Adobe recommande cette option. Si les métadonnées sont générées hors connexion, le serveur de licences n’a pas besoin d’accéder aux CEK 1.x ni aux informations d’identification de l’outil de création de package. En outre, la conversion des offres hors ligne améliore les performances car le serveur de licences n’a pas besoin de générer les métadonnées en temps réel.

* À la demande

   Générez les métadonnées Adobe Access à la demande lorsqu’un client les demande. Lorsqu’un client Adobe Access télécharge le contenu de la version 1.x, il envoie les métadonnées DRM (également connues sous le nom d’en-tête DRM) au SDK Adobe Access. Le SDK convertit les métadonnées DRM au format actuel. Le SDK chiffre et incorpore la clé de chiffrement de contenu (CEK) dans les métadonnées et renvoie le contenu au client Adobe Access. (Les métadonnées Adobe Access 1.x ne contiennent pas le CEK.)

   Pour convertir les métadonnées, Adobe Access requiert l&#39;accès aux clés de chiffrement de contenu Adobe Access 1.x. Lorsque vous effectuez une migration à partir de Flash Media Rights Management Server 1.x, vous pouvez continuer à stocker les clés de chiffrement de contenu dans la base de données LiveCycle ES ou vous pouvez mettre en oeuvre une solution personnalisée pour stocker en toute sécurité les clés de chiffrement de contenu ailleurs. Si vous choisissez de continuer à stocker les clés de chiffrement du contenu dans la base de données LiveCycle ES, suivez les recommandations décrites dans la section &quot;Protection de l’accès au contenu sensible dans la base de données&quot; dans *Renforcement et sécurité de LiveCycle ES*.

Pour plus d’informations sur la compatibilité avec le contenu compressé à l’aide de Flash Media Rights Management Server 1.x, voir le Guide de référence *de l’API* Adobe Access.
