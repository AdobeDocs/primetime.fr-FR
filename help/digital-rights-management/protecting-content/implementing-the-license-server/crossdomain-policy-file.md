---
seo-title: Fichier de stratégie DRM interdomaines
title: Fichier de stratégie DRM interdomaines
uuid: cb91a85a-1825-4fd7-a25c-880cdbd5c8b8
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Fichier de stratégie DRM interdomaines {#crossdomain-drm-policy-file}

Si le serveur de licences est hébergé sur un domaine différent de celui du fichier SWF de lecture vidéo, un fichier de stratégie DRM interdomaines ( [!DNL crossdomain.xml]) est nécessaire pour permettre au fichier SWF de demander des licences à un serveur de licences. Un fichier de stratégie DRM interdomaines est représenté par un fichier XML qui permet au serveur d’indiquer que ses données et ses  sont disponibles pour les fichiers SWF fournis à partir d’autres domaines. Tout fichier SWF diffusé à partir d’un domaine spécifié dans le fichier de stratégie DRM interdomaines du serveur de licences est autorisé à accéder aux données ou aux ressources provenant de ce serveur de licences.

Adobe recommande aux développeurs de suivre les bonnes pratiques lors du déploiement du fichier de stratégie interdomaines en autorisant uniquement les domaines de confiance à accéder au serveur de licences et en limitant l’accès au sous-répertoire de licences sur le serveur Web.

Pour plus d’informations sur les fichiers de stratégie DRM interdomaines, voir les emplacements suivants :

* Contrôles de site Web (fichiers de stratégie DRM)
* Spécification de fichier de stratégie DRM interdomaines : [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

