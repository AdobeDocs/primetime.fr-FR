---
description: Une liste autorisée est une liste d’entités de confiance.
title: Conserver une liste autorisée de packages de contenu approuvés
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Conserver une liste autorisée de packages de contenu approuvés {#maintain-a-allowlist-of-trusted-content-packagers}

Une liste autorisée est une liste d’entités de confiance.

Pour les fournisseurs de modules de contenu, les entités sont des organisations approuvées par le propriétaire du contenu pour compresser (ou chiffrer) les fichiers vidéo et créer du contenu protégé DRM. Lors du déploiement d’Adobe Primetime DRM, vous devez gérer une liste autorisée de fournisseurs de contenu approuvés. Vous devez également vérifier l’identité du module de contenu dans les métadonnées DRM d’un fichier protégé par DRM avant d’émettre une licence.

Pour savoir comment obtenir des informations sur l’entité qui a empaqueté le contenu, voir [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).
