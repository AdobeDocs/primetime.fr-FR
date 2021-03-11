---
title: Tenir à jour une liste autorisée de gestionnaires de contenu approuvés
description: Tenir à jour une liste autorisée de gestionnaires de contenu approuvés
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# Tenir à jour une liste autorisée de gestionnaires de contenu approuvés {#maintain-a-allowlist-of-trusted-content-packagers}

Une **liste autorisée** est une liste d&#39;entités approuvées. Dans le cas des packages de contenu, il s’agit d’organisations auxquelles le propriétaire du contenu fait confiance pour assembler (ou chiffrer) les fichiers vidéo FLV/F4V, ce qui crée du contenu protégé DRM. Lors du déploiement d’Adobe Access, il est recommandé de conserver une liste autorisée de gestionnaires de contenu approuvés et de vérifier l’identité du gestionnaire de contenu contenu contenu contenu contenu dans les métadonnées DRM (l’en-tête DRM) d’un fichier protégé par DRM avant de délivrer une licence.

Pour en savoir plus sur l&#39;obtention d&#39;informations sur l&#39;entité qui a inclus le contenu, voir `V2ContentMetaData.getPackagerInfo()` dans le *Guide de référence de l&#39;API d&#39;accès aux Adobes*.
