---
title: Processus CEK externe DRM AAXS
description: Ce processus diffère de la plupart des systèmes DRM existants, car il ne nécessite l'utilisation d'aucun référentiel central ou système de gestion de clés de contenu (CKMS).
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Processus CEK externe DRM AAXS{#aaxs-drm-external-cek-workflow}

Ce processus diffère de la plupart des systèmes DRM existants, car il ne nécessite pas l&#39;utilisation d&#39;un référentiel central ou d&#39;un système de gestion des clés de contenu (CKMS). Cependant, pour les clients qui souhaitent qu&#39;AAXS travaille avec leur CKMS existant, AAXS fournit une fonctionnalité appelée &quot;CEK externe&quot;, dans laquelle le CEK est fourni à l&#39;extérieur au moment de l&#39;emballage et de la délivrance des licences.

![](assets/ECEK_Workflow.PNG)

1. (Package) Le SDK Java AAXS est fourni avec un CEK et un CEK ID.
1. (Package) Le CEK est utilisé pour chiffrer le contenu.
1. (Package) L’identifiant CEK est inséré dans les métadonnées DRM du contenu.
1. L’appareil tente de lire le contenu en demandant une licence au serveur AAXS.
1. (Licence) Le serveur AAXS extrait l’identifiant CEK des métadonnées de contenu.
1. Le serveur AAXS récupère le CEK à partir du fichier CKMS.
1. (Licence) Le serveur AAXS délivre à l’appareil une licence contenant le CEK.
