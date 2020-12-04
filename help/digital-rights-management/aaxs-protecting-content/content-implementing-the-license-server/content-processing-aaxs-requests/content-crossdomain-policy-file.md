---
seo-title: Fichier de stratégie interdomaines
title: Fichier de stratégie interdomaines
uuid: fc05aa5e-6fbd-445f-a22a-f795d5a0b3ad
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# Fichier de stratégie de domaine croisé {#crossdomain-policy-file}

Si le serveur de licences est hébergé sur un domaine différent du SWF de lecture vidéo, un fichier de stratégie interdomaines (crossdomain.xml) est nécessaire pour permettre au SWF de demander des licences au serveur de licences. Un fichier de stratégie interdomaines est un fichier XML qui permet au serveur d’indiquer que ses données et documents sont disponibles pour les fichiers SWF fournis à partir d’autres domaines. Tout fichier SWF diffusé à partir d’un domaine spécifié dans le fichier de stratégie interdomaines du serveur de licences est autorisé à accéder aux données ou aux ressources provenant de ce serveur de licences.

L’Adobe recommande aux développeurs de suivre les meilleures pratiques lors du déploiement du fichier de stratégie interdomaines en autorisant uniquement les domaines approuvés à accéder au serveur de licences et en limitant l’accès au sous-répertoire de licences sur le serveur Web.

Pour plus d’informations sur les fichiers de stratégie interdomaines, voir les emplacements suivants :

* Contrôles de site Web (fichiers de stratégie)
* Spécification de fichier de stratégie interdomaines : [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

