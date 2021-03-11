---
title: Processus DRM AAXS standard
description: Processus DRM AAXS standard
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Processus DRM AAXS standard{#standard-aaxs-drm-workflow}

1. (Package) Le SDK Java AAXS génère un CEK aléatoire.
1. (Package) Le CEK est utilisé pour chiffrer le contenu.
1. (Package) Le CEK est chiffré à l’aide de la clé publique du serveur de licences AAXS.
1. (Package) Le CEK chiffré est inséré dans les métadonnées DRM du contenu.
1. L’appareil tente de lire le contenu en demandant une licence au serveur AAXS.
1. (Licence) Le serveur AAXS utilise sa clé privée pour déchiffrer le CEK à partir des métadonnées.
1. (Licence) Le serveur AAXS délivre à l’appareil une licence contenant le CEK.
