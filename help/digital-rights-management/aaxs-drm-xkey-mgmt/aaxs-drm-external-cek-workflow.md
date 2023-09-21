---
title: Processus du CEK externe AXS DRM
description: Ce workflow diffère de la plupart des systèmes DRM existants, car il ne nécessite l’utilisation d’aucun référentiel central ou système de gestion de clé de contenu (CKMS).
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Processus du CEK externe AXS DRM{#aaxs-drm-external-cek-workflow}

Ce workflow diffère de la plupart des systèmes DRM existants, car il ne nécessite l’utilisation d’aucun référentiel central ou système de gestion de clé de contenu (CKMS). Cependant, pour les clients qui souhaitent qu’AAXS fonctionne avec leur CKMS existant, AAXS fournit une fonctionnalité appelée &quot;External CEK&quot;, dans laquelle le CEK est fourni en externe au moment de l’envoi du package et de la licence.

![](assets/ECEK_Workflow.PNG)

1. (Package) Le SDK Java AAXS est fourni avec un CEK et un CEK ID.
1. (Package) Le CEK est utilisé pour chiffrer le contenu.
1. (Package) L’ID CEK est inséré dans les métadonnées DRM du contenu.
1. L’appareil tente de lire le contenu en demandant une licence au serveur AAXS.
1. (Licences) Le serveur AXS extrait l’ID CEK des métadonnées de contenu.
1. Le serveur AXS récupère le CEK à partir du CKMS.
1. (Licences) Le serveur AXS délivre à l’appareil une licence contenant le CEK.
