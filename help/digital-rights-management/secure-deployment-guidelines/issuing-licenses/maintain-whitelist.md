---
description: Une liste autorisée est une liste d'entités de confiance.
seo-description: Une liste autorisée est une liste d'entités de confiance.
seo-title: Tenir à jour une liste autorisée de gestionnaires de contenu approuvés
title: Tenir à jour une liste autorisée de gestionnaires de contenu approuvés
uuid: 9a132ef9-eb56-408a-939e-1acd32d83a33
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Tenir à jour une liste autorisée de gestionnaires de contenu approuvés {#maintain-a-allowlist-of-trusted-content-packagers}

Une liste autorisée est une liste d&#39;entités de confiance.

Pour les gestionnaires de packages de contenu, les entités sont des organisations dont le propriétaire du contenu fait confiance pour assembler (ou chiffrer) les fichiers vidéo et créer du contenu protégé DRM. Lors du déploiement de Adobe Primetime DRM, vous devez conserver une liste autorisée de gestionnaires de contenu approuvés. Vous devez également vérifier l’identité du gestionnaire de contenu dans les métadonnées DRM d’un fichier protégé par DRM avant d’émettre une licence.

Pour savoir comment obtenir des informations sur l’entité qui a conditionné le contenu, voir [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).
