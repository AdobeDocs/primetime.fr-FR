---
description: Le service de reconditionnement de contenu créatif (CRS) garantit qu’un créatif publicitaire non HLS peut être lu correctement dans les flux HLS. Le serveur de manifeste appelle CRS lorsqu’il rencontre une publicité non HLS.
title: Présentation des CRS
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Présentation des CRS {#overview-of-crs}

Le service de reconditionnement de contenu créatif (CRS) garantit qu’un créatif publicitaire non HLS peut être lu correctement dans les flux HLS. Le serveur de manifeste appelle CRS lorsqu’il rencontre une publicité non HLS.

>[!NOTE]
>
>Par défaut, CRS est désactivé. Pour activer CRS pour votre compte, contactez votre gestionnaire de compte technique d’Adobe.
>
>Pour plus d’informations sur l’activation de CRS dans les applications TVSDK, voir *Activation de CRS dans les applications TVSDK* dans le Guide du programmeur de votre plateforme. Par exemple, pour Android 3.4, voir [Activation de CRS dans les applications TVSDK](../../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-transcoding/android-3x-ad-transcoding.md)

CRS prépare les éléments créatifs publicitaires HTTP Live Streaming (HLS) pour le flux de contenu et injecte des paquets ID3 pour le suivi des publicités côté client. Il transcode les fichiers MP4, FLV et WebM reçus de serveurs de publicités tiers, de réseaux publicitaires et de serveurs d’agences au format HLS.

Lorsque l’insertion de publicités Adobe Primetime rencontre un contenu publicitaire non HLS, elle l’envoie à CRS pour le reconditionnement, qui ne dure généralement pas plus de trois minutes. CRS envoie la publicité transcodée au serveur CDN pour une utilisation ultérieure. Cela s’appelle **`just-in-time (JIT) repackaging`**. Vous pouvez également transcoder les éléments créatifs publicitaires avant qu’ils ne soient nécessaires à l’aide de la variable  [API de réparation](../../primetime-ad-insertion/~old-creative-repackaging-service/api-repackage.md) . Cela s’appelle *`asynchronous repackaging`*.

Votre gestionnaire de compte technique Adobe peut également modifier certains comportements par défaut CRS si un autre comportement est mieux adapté à votre application. Ces éléments sont les suivants :

* Priorité des formats de création publicitaire.

  La variable `MediaFiles` d’une réponse VAST/VMAP peut contenir des éléments créatifs avec différentes `MediaFile` types. Par défaut, le serveur manifeste en sélectionne un selon un ensemble fixe de priorités ( `application/x-mpegURL`, `application/vnd.apple.mpegURL`, `video/mp4`, `video/x-flv,video/webm`). Adobe peut modifier les priorités de votre compte.
* Durée de la cible de l’annonce.

  Le serveur de manifeste détecte la durée de la publicité cible à partir de la liste de lecture du contenu et l’envoie à CRS. Adobe peut modifier ce comportement, de sorte que CRS utilise toujours une durée fixe que vous indiquez pour votre compte.
