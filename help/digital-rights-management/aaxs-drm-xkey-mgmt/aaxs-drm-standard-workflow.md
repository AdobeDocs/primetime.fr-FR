---
title: Processus DRM AXS standard
description: Processus DRM AXS standard
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# Processus DRM AXS standard{#standard-aaxs-drm-workflow}

1. (Package) Le SDK Java AAXS génère un CEK aléatoire.
1. (Package) Le CEK est utilisé pour chiffrer le contenu.
1. (Package) Le CEK est chiffré à l’aide de la clé publique du serveur de licences AAXS.
1. (Package) Le CEK chiffré est inséré dans les métadonnées DRM du contenu.
1. L’appareil tente de lire le contenu en demandant une licence au serveur AAXS.
1. (Licences) Le serveur AXS utilise sa clé privée pour déchiffrer le CEK à partir des métadonnées.
1. (Licences) Le serveur AXS délivre à l’appareil une licence contenant le CEK.
