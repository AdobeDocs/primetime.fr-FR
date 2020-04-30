---
description: Vous pouvez mettre en oeuvre plusieurs solutions DRM pour vos applications TVSDK à l’aide de Primetime DRM Cloud, proposé par ExpressPlay. Les solutions DRM incluent le FairPlay d'Apple, le widevine de Google, le PlayReady de Microsoft et Primetime Access d'Adobe.
seo-description: Vous pouvez mettre en oeuvre plusieurs solutions DRM pour vos applications TVSDK à l’aide de Primetime DRM Cloud, proposé par ExpressPlay. Les solutions DRM incluent le FairPlay d'Apple, le widevine de Google, le PlayReady de Microsoft et Primetime Access d'Adobe.
seo-title: Présentation de la gestion multiDRM
title: Présentation de la gestion multiDRM
uuid: 1705a338-baeb-4fcd-ae16-08963da55ab8
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Workflows multiDRM {#multi-drm-workflows}

Vous pouvez mettre en oeuvre plusieurs solutions DRM pour vos applications TVSDK à l’aide de Primetime DRM Cloud, proposé par ExpressPlay. Les solutions DRM incluent le FairPlay d&#39;Apple, le widevine de Google, le PlayReady de Microsoft et Primetime Access d&#39;Adobe.

## Présentation de la gestion multiDRM {#multi-drm-overview}

Adobe TVSDK prend en charge la protection DRM à l’aide de plusieurs modèles DRM. Adobe offres *Primetime DRM Cloud, optimisé par ExpressPlay* pour fournir le conditionnement, la licence et la lecture de votre contenu vidéo sur plusieurs plates-formes.

Les modèles DRM pris en charge incluent le DRM (AAXS) d’Adobe *Primetime Access* , ainsi que des DRM natifs sur divers périphériques, notamment [Widevine](https://www.widevine.com) sur Chrome et Android, [FairPlay](https://developer.apple.com/streaming/fps/) sur Safari et iOS et [PlayReady sur Edge et XboxOne. ](https://www.microsoft.com/playready/) Consultez un représentant Adobe pour savoir quels schémas DRM sont actuellement disponibles sur ces plates-formes, ainsi que les dates prévues des prochaines versions.

TVSDK prend en charge les licences DRM émises par tout serveur de licences utilisant ces protocoles. Outre la prise en charge de plusieurs solutions DRM, Adobe offres *Primetime DRM Cloud, optimisé par ExpressPlay* en tant que solution dans laquelle ExpressPlay exploite les serveurs de licences pour chaque solution. Cela peut simplifier la configuration et la maintenance de vos besoins de délivrance de licences DRM.

Pour utiliser *Primetime DRM Cloud, optimisé par ExpressPlay* pour la mise en oeuvre de vos besoins DRM dans les applications TVSDK, vous devez d’abord obtenir un compte [ExpressPlay.com](https://www.expressplay.com) . ExpressPlay offre la possibilité d&#39;obtenir des licences pour plusieurs systèmes de protection DRM différents, et fournit également d&#39;autres services, notamment l&#39;emballage et la gestion des clés.

Votre représentant Adobe va d’abord configurer votre compte ExpressPlay. Vous pouvez ensuite configurer votre compte et obtenir les authentificateurs ** clients que vous utiliserez dans les demandes de jeton de licence aux serveurs ExpressPlay.