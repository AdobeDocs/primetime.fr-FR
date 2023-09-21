---
title: Fichier de stratégie interdomaine
description: Fichier de stratégie interdomaine
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Fichier de stratégie interdomaine {#crossdomain-policy-file}

Si le serveur de licences est hébergé sur un domaine différent de celui du SWF de lecture vidéo, un fichier de stratégie interdomaines (crossdomain.xml) est nécessaire pour permettre au SWF de demander des licences au serveur de licences. Un fichier de stratégie interdomaines est un fichier XML qui permet au serveur d’indiquer que ses données et documents sont disponibles pour les fichiers SWF diffusés à partir d’autres domaines. Tout fichier de SWF provenant d’un domaine spécifié dans le fichier de stratégie interdomaines du serveur de licences est autorisé à accéder aux données ou aux ressources provenant de ce serveur de licences.

Adobe recommande aux développeurs de suivre les bonnes pratiques lors du déploiement du fichier de stratégie inter-domaines en autorisant uniquement les domaines approuvés à accéder au serveur de licences et en limitant l’accès au sous-répertoire de licence sur le serveur web.

Pour plus d’informations sur les fichiers de stratégie inter-domaines, reportez-vous aux emplacements suivants :

* Contrôles de site web (fichiers de stratégie)
* Spécification de fichier de stratégie inter-domaines : [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)
