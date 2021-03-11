---
description: Une liste autorisée est une liste d'entités de confiance.
title: Tenir à jour une liste autorisée de gestionnaires de contenu approuvés
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Tenir à jour une liste autorisée de gestionnaires de contenu approuvés {#maintain-a-allowlist-of-trusted-content-packagers}

Une liste autorisée est une liste d&#39;entités de confiance.

Pour les gestionnaires de packages de contenu, les entités sont des organisations dont le propriétaire du contenu fait confiance pour assembler (ou chiffrer) les fichiers vidéo et créer du contenu protégé DRM. Lors du déploiement de Adobe Primetime DRM, vous devez conserver une liste autorisée de gestionnaires de contenu approuvés. Vous devez également vérifier l’identité du gestionnaire de contenu dans les métadonnées DRM d’un fichier protégé par DRM avant d’émettre une licence.

Pour savoir comment obtenir des informations sur l’entité qui a conditionné le contenu, voir [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).
