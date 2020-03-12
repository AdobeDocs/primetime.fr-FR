---
seo-title: Processus DRM AAXS standard
title: Processus DRM AAXS standard
description: Processus DRM AAXS standard
seo-description: Processus DRM AAXS standard
uuid: b996eb2c-8e37-4a29-a972-e09c69d2461d
translation-type: tm+mt
source-git-commit: 17a492d30c65b1b5e12419f04afa0116654b99fc

---


# Processus DRM AAXS standard{#standard-aaxs-drm-workflow}

1. (Package) Le SDK Java AAXS génère un CEK aléatoire.
1. (Package) Le CEK est utilisé pour chiffrer le contenu.
1. (Package) Le CEK est chiffré à l’aide de la clé publique AAXS License Server.
1. (Package) Le CEK chiffré est inséré dans les métadonnées DRM du contenu.
1. Le périphérique tente de lire le contenu en demandant une licence au serveur AAXS.
1. (Licence) Le serveur AAXS utilise sa clé privée pour déchiffrer le CEK à partir des métadonnées.
1. (Licence) Le serveur AAXS délivre au périphérique une licence contenant le CEK.
