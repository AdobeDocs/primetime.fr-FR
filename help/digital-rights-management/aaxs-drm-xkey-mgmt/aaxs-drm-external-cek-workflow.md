---
seo-title: Flux de travaux CEK externe AXS DRM
title: Flux de travaux CEK externe AXS DRM
description: Ce flux de travail diffère de la plupart des systèmes DRM existants, car il ne nécessite l’utilisation d’aucun référentiel central ou système de gestion des clés de contenu (CKMS).
seo-description: Ce flux de travail diffère de la plupart des systèmes DRM existants, car il ne nécessite l’utilisation d’aucun référentiel central ou système de gestion des clés de contenu (CKMS).
uuid: b313594b-0feb-4f27-bf02-f04b955e2140
translation-type: tm+mt
source-git-commit: 17a492d30c65b1b5e12419f04afa0116654b99fc

---


# Flux de travaux CEK externe AXS DRM{#aaxs-drm-external-cek-workflow}

Ce flux de travail diffère de la plupart des systèmes DRM existants, car il ne nécessite l’utilisation d’aucun référentiel central ou système de gestion des clés de contenu (CKMS). Toutefois, pour les clients qui souhaitent qu’AAXS travaille avec leur CKMS existant, AAXS fournit une fonctionnalité appelée &quot;External CEK&quot;, dans laquelle le CEK est fourni en externe au moment de l’emballage et de la délivrance de la licence.

![](assets/ECEK_Workflow.PNG)

1. (Package) Le SDK Java AAXS est fourni avec un CEK et un ID CEK.
1. (Package) Le CEK est utilisé pour chiffrer le contenu.
1. (Package) L’identifiant CEK est inséré dans les métadonnées DRM du contenu.
1. Le périphérique tente de lire le contenu en demandant une licence au serveur AAXS.
1. (Licence) Le serveur AAXS extrait l’identifiant CEK des métadonnées de contenu.
1. Le serveur AAXS récupère le CEK du fichier CKMS.
1. (Licence) Le serveur AAXS délivre au périphérique une licence contenant le CEK.
