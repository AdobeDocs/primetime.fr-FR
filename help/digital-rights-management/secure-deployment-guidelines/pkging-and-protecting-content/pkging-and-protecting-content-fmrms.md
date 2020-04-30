---
description: Flash Media Rights Management Server 1.x et Adobe Primetime DRM utilisent des métadonnées différentes pour regrouper le contenu et demander des licences. Pour que Primetime DRM utilise le contenu FMRMS version 1.x, les métadonnées doivent être converties.
seo-description: Flash Media Rights Management Server 1.x et Adobe Primetime DRM utilisent des métadonnées différentes pour regrouper le contenu et demander des licences. Pour que Primetime DRM utilise le contenu FMRMS version 1.x, les métadonnées doivent être converties.
seo-title: Assurer la compatibilité avec Flash Media Rights Management Server 1.x
title: Assurer la compatibilité avec Flash Media Rights Management Server 1.x
uuid: dd70941e-9015-4fb0-b265-557b6252e051
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Assurer la compatibilité avec Flash Media Rights Management Server 1.x {#ensuring-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.x et Adobe Primetime DRM utilisent des métadonnées différentes pour regrouper le contenu et demander des licences. Pour que Primetime DRM utilise le contenu FMRMS version 1.x, les métadonnées doivent être converties.

Le SDK DRM de Primetime prend en charge les options suivantes pour la conversion des métadonnées :

* Hors ligne (recommandé)

   Générez les métadonnées DRM Primetime dans un processus hors ligne et stockez-les jusqu’à ce qu’elles soient demandées par un client. Si les métadonnées sont générées hors connexion, le serveur de licences n’a pas besoin d’accéder aux CEK 1.x ni aux informations d’identification de l’outil de création de package. La conversion des offres hors ligne améliore les performances, car le serveur de licences n’a pas besoin de générer les métadonnées en temps réel.
* À la demande

   Les métadonnées DRM Primetime sont générées lorsque les métadonnées sont demandées par un client. Lorsqu’un client DRM Primetime télécharge le contenu de la version 1.x, le client envoie les métadonnées DRM au SDK DRM Primetime. Le SDK convertit les métadonnées DRM au format actuel, chiffre et incorpore la clé de chiffrement de contenu (CEK) dans les métadonnées et renvoie le contenu au client DRM Primetime.

   >[!NOTE]
   >
   >Les métadonnées DRM 1.x de Primetime n’incluent pas le CEK.

   Pour convertir les métadonnées, Primetime DRM nécessite l’accès aux clés de chiffrement de contenu DRM 1.x de Primetime. Lorsque vous effectuez une migration à partir de Flash Media Rights Management Server 1.x, vous pouvez continuer à stocker les clés de chiffrement de contenu dans la base de données LiveCycle ES ou mettre en oeuvre une solution personnalisée pour stocker en toute sécurité les clés de chiffrement de contenu à un autre emplacement. Si vous décidez de stocker les clés de chiffrement du contenu dans la base de données LiveCycle ES, suivez les recommandations décrites dans la section *Protection de l’accès au contenu sensible dans la base de données* dans **Renforcement et sécurité de LiveCycle® ES2**.

Pour plus d’informations sur la compatibilité avec le contenu compressé à l’aide de Flash Media Rights Management Server 1.x, voir les API DRM d’Adobe Primetime sur Références [de l’API](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References)Adobe Primetime.
