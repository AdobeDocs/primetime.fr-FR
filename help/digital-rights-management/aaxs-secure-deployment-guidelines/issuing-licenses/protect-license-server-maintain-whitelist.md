---
seo-title: Tenir à jour une liste blanche des gestionnaires de contenu approuvés
title: Tenir à jour une liste blanche des gestionnaires de contenu approuvés
uuid: ad40993c-15c3-43b2-9593-7b75802cfe69
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Tenir à jour une liste blanche des gestionnaires de contenu approuvés{#maintain-a-whitelist-of-trusted-content-packagers}

Une *liste blanche* est une liste d&#39;entités de confiance. Dans le cas des packages de contenu, il s’agit d’organisations auxquelles le propriétaire du contenu fait confiance pour assembler (ou chiffrer) les fichiers vidéo FLV/F4V, ce qui crée du contenu protégé DRM. Lors du déploiement d’Adobe Access, il est recommandé de conserver une liste blanche des packages de contenu de confiance et de vérifier l’identité du gestionnaire de contenu contenu contenu contenu contenu dans les métadonnées DRM (l’en-tête DRM) d’un fichier protégé par DRM avant d’émettre une licence.

Pour en savoir plus sur l’obtention d’informations sur l’entité qui a inclus le contenu, voir `V2ContentMetaData.getPackagerInfo()` la référence *de l’API* Adobe Access.
