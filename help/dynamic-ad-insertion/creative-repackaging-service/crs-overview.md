---
description: Le service de reconditionnement de création (CRS) garantit qu’un créatif non-HLS peut lire correctement les flux HLS. Le serveur de manifeste appelle CRS lorsqu’il rencontre une publicité non-HLS.
seo-description: Le service de reconditionnement de création (CRS) garantit qu’un créatif non-HLS peut lire correctement les flux HLS. Le serveur de manifeste appelle CRS lorsqu’il rencontre une publicité non-HLS.
seo-title: Aperçu du CS Ex
title: Aperçu du CS Ex
uuid: 3ae75fa7-397f-47ba-8e3d-50543ca25458
translation-type: tm+mt
source-git-commit: 4788a8de8ba47d7f448967066e1bd0fb73fdb7a8

---


# Aperçu du CS Ex {#overview-of-crs}

Le service de reconditionnement de création (CRS) garantit qu’un créatif non-HLS peut lire correctement les flux HLS. Le serveur de manifeste appelle CRS lorsqu’il rencontre une publicité non-HLS.

>[!NOTE]
>
>Par défaut, CRS est désactivé. Pour activer CRS pour votre compte, contactez votre gestionnaire de compte technique Adobe.
>
>Pour plus d’informations sur l’activation du CRS dans les applications TVSDK, consultez la rubrique *Activer le CRS dans les applications* TVSDK dans le Guide du programmeur de votre plate-forme. Par exemple, pour Android 3.4, voir [Activation de CRS dans les applications TVSDK](../../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-transcoding/android-3x-ad-transcoding.md)

CRS prépare les éléments créatifs de la publicité HTTP Live Streaming (HLS) pour le flux de contenu et injecte des paquets ID3 pour le suivi des publicités côté client. Il transcode les fichiers MP4, FLV et WebM reçus de serveurs publicitaires tiers, de réseaux publicitaires et de serveurs d’agences au format HLS.

Lorsque l’insertion d’une publicité Adobe Primetime rencontre un élément créatif publicitaire non-HLS, elle l’envoie à CRS pour le reconditionnement, qui ne dure généralement pas plus de trois minutes. CRS envoie la publicité transcodée et créative au serveur CDN pour une utilisation ultérieure. Ça s&#39;appelle **`just-in-time (JIT) repackaging`**. Vous pouvez également transcoder les éléments créatifs publicitaires avant qu’ils ne soient nécessaires à l’aide de l’API [](../../dynamic-ad-insertion/creative-repackaging-service/api-repackage.md) de reconditionnement. Ça s&#39;appelle *`asynchronous repackaging`*.

Votre gestionnaire de compte technique Adobe peut également modifier certains comportements par défaut CRS si un autre comportement convient mieux à votre application. Voici :

* Priorité des formats de création publicitaire.

   La `MediaFiles` section d’une réponse VAST/VMAP peut contenir des éléments créatifs de différents `MediaFile` types. Par défaut, le serveur de manifeste en sélectionne un en fonction d’un jeu de priorités fixe ( `application/x-mpegURL`, `application/vnd.apple.mpegURL`, `video/mp4`, `video/x-flv,video/webm`). Adobe peut modifier les priorités de votre compte.
* Durée  la publicité.

   Le serveur de manifeste détecte la durée de la publicité  dans la liste de lecture du contenu et l’envoie à CRS. Adobe peut modifier ce comportement afin que CRS utilise toujours une durée fixe que vous spécifiez pour votre compte.
