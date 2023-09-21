---
description: Flash Media Rights Management Server 1.x et Adobe Primetime DRM utilisent différentes métadonnées pour regrouper le contenu et demander des licences. Pour que Primetime DRM utilise le contenu FMRMS version 1.x, les métadonnées doivent être converties.
title: Garantir la compatibilité avec Flash Media Rights Management Server 1.x
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Garantir la compatibilité avec Flash Media Rights Management Server 1.x {#ensuring-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.x et Adobe Primetime DRM utilisent différentes métadonnées pour regrouper le contenu et demander des licences. Pour que Primetime DRM utilise le contenu FMRMS version 1.x, les métadonnées doivent être converties.

Le SDK DRM Primetime prend en charge les options suivantes pour la conversion des métadonnées :

* Hors ligne (recommandé)

  Générez les métadonnées DRM Primetime dans un processus hors ligne et stockez les métadonnées jusqu’à ce qu’elles soient demandées par un client. Si les métadonnées sont générées hors ligne, le serveur de licences n’a pas besoin d’accéder aux CEK 1.x ni aux informations d’identification de packager. La conversion hors ligne offre de meilleures performances, car le serveur de licences n’a pas besoin de générer les métadonnées en temps réel.
* À la demande

  Les métadonnées DRM Primetime sont générées lorsque les métadonnées sont demandées par un client. Lorsqu’un client DRM Primetime télécharge le contenu de la version 1.x, le client envoie les métadonnées DRM au SDK DRM Primetime. Le SDK convertit les métadonnées DRM au format actuel, chiffre et incorpore la clé de chiffrement de contenu (CEK) dans les métadonnées et renvoie le contenu au client DRM Primetime.

  >[!NOTE]
  >
  >Les métadonnées Primetime DRM 1.x n’incluent pas le CEK.

  Pour convertir les métadonnées, Primetime DRM nécessite l’accès aux clés de chiffrement de contenu Primetime DRM 1.x. Lorsque vous migrez depuis Flash Media Rights Management Server 1.x, vous pouvez continuer à stocker les clés de chiffrement de contenu dans la base de données LiveCycle ES ou mettre en oeuvre une solution personnalisée pour stocker les clés de chiffrement de contenu en toute sécurité à un autre emplacement. Si vous décidez de stocker les clés de chiffrement du contenu dans la base de données ES de LiveCycle, suivez les recommandations décrites dans la section *Protection de l&#39;accès aux contenus sensibles dans la base* in **Renforcement et sécurité de LiveCycle® ES2**.

Pour plus d’informations sur la compatibilité avec le contenu empaqueté à l’aide de Flash Media Rights Management Server 1.x, voir API Adobe Primetime DRM sur [Références de l’API Adobe Primetime](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References).
