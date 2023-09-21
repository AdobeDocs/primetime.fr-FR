---
description: Vous pouvez mettre en oeuvre plusieurs solutions DRM pour vos applications TVSDK à l’aide de Primetime DRM Cloud, optimisé par ExpressPlay. Les solutions DRM incluent Apple FairPlay, Google Widevine, Microsoft PlayReady et Primetime Access d’Adobe.
title: Présentation multi-DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Processus multi-DRM {#multi-drm-workflows}

Vous pouvez mettre en oeuvre plusieurs solutions DRM pour vos applications TVSDK à l’aide de Primetime DRM Cloud, optimisé par ExpressPlay. Les solutions DRM incluent Apple FairPlay, Google Widevine, Microsoft PlayReady et Primetime Access d’Adobe.

## Présentation multi-DRM {#multi-drm-overview}

Adobe TVSDK prend en charge la protection DRM à l’aide de plusieurs schémas DRM. Offres Adobe *Primetime DRM Cloud, optimisé par ExpressPlay* pour fournir un package, des licences et la lecture de votre contenu vidéo sur plusieurs plateformes.

Les schémas DRM pris en charge incluent les Adobes *Accès Primetime* DRM (AAXS), ainsi que des DRM natifs sur divers appareils, y compris [Widevine](https://www.widevine.com) sur Chrome et Android, [FairPlay](https://developer.apple.com/streaming/fps/) sous Safari et iOS, et [PlayReady](https://www.microsoft.com/playready/) sur Edge et XboxOne. Consultez le représentant des Adobes pour savoir quels schémas DRM sont actuellement disponibles sur ces plateformes, ainsi que les dates prévues des prochaines versions.

TVSDK prend en charge les licences DRM émises par n’importe quel serveur de licences utilisant ces protocoles. Outre la prise en charge de plusieurs solutions DRM, les offres Adobe *Primetime DRM Cloud, optimisé par ExpressPlay* en tant que solution dans laquelle ExpressPlay utilise les serveurs de licences pour chaque solution. Cela peut simplifier la configuration et la maintenance de vos besoins en matière d’octroi de licence DRM.

Pour utiliser *Primetime DRM Cloud, optimisé par ExpressPlay* pour mettre en oeuvre vos besoins DRM dans les applications TVSDK, vous devez d’abord obtenir une [ExpressPlay.com](https://www.expressplay.com) compte . ExpressPlay offre la possibilité d’obtenir des licences pour plusieurs programmes de protection DRM, et fournit également d’autres services, notamment la gestion des emballages et des clés.

Votre représentant d’Adobe configurera tout d’abord votre compte ExpressPlay. Vous pouvez ensuite configurer votre compte et obtenir la variable *authentificateurs de clients* que vous utiliserez dans les demandes de jetons de licence aux serveurs ExpressPlay.
