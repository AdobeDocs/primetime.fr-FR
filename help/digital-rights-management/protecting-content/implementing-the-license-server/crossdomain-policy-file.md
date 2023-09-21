---
title: Fichier de stratégie DRM interdomaine
description: Fichier de stratégie DRM interdomaine
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Fichier de stratégie DRM interdomaine {#crossdomain-drm-policy-file}

Si le serveur de licences est hébergé sur un domaine différent du SWF de lecture vidéo, un fichier de stratégie DRM interdomaines ( [!DNL crossdomain.xml]) est nécessaire pour permettre au SWF de demander des licences à un serveur de licences. Un fichier de stratégie DRM interdomaines est représenté par un fichier XML qui permet au serveur d’indiquer que ses données et documents sont disponibles pour les fichiers SWF diffusés à partir d’autres domaines. Tout fichier de SWF provenant d’un domaine spécifié dans le fichier de stratégie DRM interdomaines du serveur de licences est autorisé à accéder aux données ou aux ressources provenant de ce serveur de licences.

Adobe recommande aux développeurs de suivre les bonnes pratiques lors du déploiement du fichier de stratégie inter-domaines en autorisant uniquement les domaines approuvés à accéder au serveur de licences et en limitant l’accès au sous-répertoire de licence sur le serveur web.

Pour plus d’informations sur les fichiers de stratégie DRM interdomaines, voir les emplacements suivants :

* Contrôles de site web (fichiers de stratégie DRM)
* Spécification de fichier de stratégie DRM interdomaines : [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

