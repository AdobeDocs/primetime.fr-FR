---
description: Le navigateur TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 originaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. Le kit TVSDK du navigateur prend en charge un ensemble dynamique de profils de débit binaire lorsque les profils apparaissent ou disparaissent du manifeste principal, y compris les débits binaires des profils non superposés entre les mises à jour.
seo-description: Le navigateur TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 originaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. Le kit TVSDK du navigateur prend en charge un ensemble dynamique de profils de débit binaire lorsque les profils apparaissent ou disparaissent du manifeste principal, y compris les débits binaires des profils non superposés entre les mises à jour.
seo-title: Mise à jour du manifeste principal en direct
title: Mise à jour du manifeste principal en direct
uuid: 4b918a73-dacf-465a-82d6-404c6bdb01f2
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise à jour du manifeste principal en direct{#live-master-manifest-update}

Le navigateur TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 originaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. Le kit TVSDK du navigateur prend en charge un ensemble dynamique de profils de débit binaire lorsque les profils apparaissent ou disparaissent du manifeste principal, y compris les débits binaires des profils non superposés entre les mises à jour.

Les fonctionnalités suivantes sont prises en charge :

* Nombre de Profils (augmentation ou diminution)
* Débit du Profil (chevauchement ou non)
* Profils avec des URL sur le même (ou sur des serveurs différents)
* Toute structure de basculement

Toutes les conditions suivantes doivent être remplies :

* Le flux est en direct.
* Le temps et l&#39;étag changent.
* Toutes les informations sur le rendu restent les mêmes (sauf que les URL peuvent varier).
* Les informations d’accès DRM restent les mêmes.
* Les segments sont regroupés autour des mêmes limites PTS et cadres dans une petite plage d’erreurs.

