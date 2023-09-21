---
title: Conserver une liste autorisée de packages de contenu approuvés
description: Conserver une liste autorisée de packages de contenu approuvés
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Conserver une liste autorisée de packages de contenu approuvés {#maintain-a-allowlist-of-trusted-content-packagers}

Un **liste autorisée** est une liste d’entités de confiance. Dans le cas des packages de contenu, il s’agit des organisations approuvées par le propriétaire du contenu pour empaqueter (ou chiffrer) les fichiers vidéo FLV/F4V, créant ainsi du contenu protégé par DRM. Lors du déploiement de Adobe Access, il est recommandé de conserver une liste autorisée de fournisseurs de contenu approuvés et de vérifier l’identité du fournisseur de contenu contenu contenu contenu dans les métadonnées DRM (l’en-tête DRM) d’un fichier protégé par DRM avant d’émettre une licence.

Pour en savoir plus sur l’obtention d’informations sur l’entité qui a empaqueté le contenu, voir `V2ContentMetaData.getPackagerInfo()` dans le *Référence de l’API Adobe Access*.
