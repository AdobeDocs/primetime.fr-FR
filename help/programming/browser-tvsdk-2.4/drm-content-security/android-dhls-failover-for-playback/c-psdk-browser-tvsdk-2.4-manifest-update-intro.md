---
description: Le navigateur TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 principaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. Le TVSDK du navigateur prend en charge un ensemble dynamique de profils de débit au fur et à mesure que les profils apparaissent ou disparaissent du manifeste principal, y compris les débits de profil non chevauchants entre les mises à jour.
title: Mise à jour du manifeste principal en direct
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---

# Mise à jour du manifeste principal en direct{#live-master-manifest-update}

Le navigateur TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 principaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. Le TVSDK du navigateur prend en charge un ensemble dynamique de profils de débit au fur et à mesure que les profils apparaissent ou disparaissent du manifeste principal, y compris les débits de profil non chevauchants entre les mises à jour.

Les fonctionnalités suivantes sont prises en charge :

* Nombre de profils (augmentation ou diminution)
* Débit binaire du profil (chevauchement ou non)
* Profils avec des URL sur le même (ou sur des serveurs différents)
* Toute structure de basculement

Toutes les conditions suivantes doivent être remplies :

* Le flux est en direct.
* L&#39;heure et l&#39;etag ont changé.
* Toutes les informations de rendu restent identiques (sauf que les URL peuvent varier).
* Les informations d’accès DRM restent identiques.
* Les segments sont conditionnés autour des mêmes limites de texte et de cadre dans une petite plage d’erreurs.
