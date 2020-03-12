---
description: Une liste blanche est un d’entités de confiance.
seo-description: Une liste blanche est un d’entités de confiance.
seo-title: Tenir à jour une liste blanche des gestionnaires de contenu approuvés
title: Tenir à jour une liste blanche des gestionnaires de contenu approuvés
uuid: 9a132ef9-eb56-408a-939e-1acd32d83a33
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Tenir à jour une liste blanche des gestionnaires de contenu approuvés{#maintain-a-whitelist-of-trusted-content-packagers}

Une liste blanche est un d’entités de confiance.

Pour les gestionnaires de contenu, les entités sont des organisations auxquelles le propriétaire du contenu fait confiance pour assembler (ou chiffrer) les fichiers vidéo et créer du contenu protégé DRM. Lors du déploiement d’Adobe Primetime DRM, vous devez conserver une liste blanche des gestionnaires de contenu approuvés. Vous devez également vérifier l’identité du gestionnaire de contenu dans les métadonnées DRM d’un fichier protégé DRM avant d’émettre une licence.

Pour savoir comment obtenir des informations sur l’entité qui a compressé le contenu, voir [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).
