---
seo-title: Tenir à jour une liste autorisée de gestionnaires de contenu approuvés
title: Tenir à jour une liste autorisée de gestionnaires de contenu approuvés
uuid: ad40993c-15c3-43b2-9593-7b75802cfe69
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Tenir à jour une liste autorisée de gestionnaires de contenu approuvés{#maintain-a-allowlist-of-trusted-content-packagers}

Une *liste autorisée* est une liste d&#39;entités approuvées. Dans le cas des packages de contenu, il s’agit d’organisations auxquelles le propriétaire du contenu fait confiance pour assembler (ou chiffrer) les fichiers vidéo FLV/F4V, ce qui crée du contenu protégé DRM. Lors du déploiement d’Adobe Access, il est recommandé de conserver une liste autorisée de gestionnaires de contenu approuvés et de vérifier l’identité du gestionnaire de contenu contenu contenu contenu contenu dans les métadonnées DRM (l’en-tête DRM) d’un fichier protégé par DRM avant de délivrer une licence.

Pour en savoir plus sur l’obtention d’informations sur l’entité qui a inclus le contenu, voir `V2ContentMetaData.getPackagerInfo()` le Guide de référence *de l’API d’accès à* Adobe.
