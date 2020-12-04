---
description: Le service de reconditionnement créatif (CRS) garantit qu’un créatif non-HLS peut lire correctement dans les flux HLS. Le serveur de manifeste appelle CRS lorsqu’il rencontre une publicité non HLS.
seo-description: Le service de reconditionnement créatif (CRS) garantit qu’un créatif non-HLS peut lire correctement dans les flux HLS. Le serveur de manifeste appelle CRS lorsqu’il rencontre une publicité non HLS.
seo-title: Vue d'ensemble des SIR
title: Vue d'ensemble des SIR
uuid: 3ae75fa7-397f-47ba-8e3d-50543ca25458
translation-type: tm+mt
source-git-commit: 4788a8de8ba47d7f448967066e1bd0fb73fdb7a8
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# Présentation du CS Ex {#overview-of-crs}

Le service de reconditionnement créatif (CRS) garantit qu’un créatif non-HLS peut lire correctement dans les flux HLS. Le serveur de manifeste appelle CRS lorsqu’il rencontre une publicité non HLS.

>[!NOTE]
>
>Par défaut, CRS est désactivé. Pour activer CRS pour votre compte, contactez votre gestionnaire de compte technique Adobe.
>
>Pour plus d&#39;informations sur l&#39;activation de CRS dans les applications TVSDK, consultez la rubrique *Activer CRS dans les applications TVSDK* du Guide du programmeur de votre plate-forme. Par exemple, pour Android 3.4, voir [Activer CRS dans les applications TVSDK](../../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-transcoding/android-3x-ad-transcoding.md)

CRS prépare les éléments créatifs de la publicité HTTP Live Streaming (HLS) pour le flux de contenu et injecte des paquets ID3 pour le suivi des publicités côté client. Il transcode au format HLS les fichiers MP4, FLV et WebM reçus de serveurs d’annonces tiers, de réseaux publicitaires et de serveurs d’agences.

Lorsque l’insertion d’une publicité Adobe Primetime rencontre un élément créatif publicitaire non HLS, elle l’envoie à CRS pour le reconditionnement, qui ne prend généralement pas plus de trois minutes. CRS envoie la publicité transcodée et créative au serveur CDN pour une utilisation ultérieure. Il s&#39;appelle **`just-in-time (JIT) repackaging`**. Vous pouvez également transcoder les éléments créatifs publicitaires avant qu’ils ne soient nécessaires à l’aide de l’[API de reconditionnement](../../dynamic-ad-insertion/creative-repackaging-service/api-repackage.md). Il s&#39;appelle *`asynchronous repackaging`*.

Votre gestionnaire de compte technique Adobe peut également modifier certains comportements par défaut CRS si un autre comportement convient mieux à votre application. Voici :

* Priorité des formats publicitaires créatifs.

   La section `MediaFiles` d&#39;une réponse VAST/VMAP peut contenir des éléments créatifs de différents types `MediaFile`. Par défaut, le serveur de manifeste en sélectionne un selon un ensemble de priorités fixe ( `application/x-mpegURL`, `application/vnd.apple.mpegURL`, `video/mp4`, `video/x-flv,video/webm`). L’Adobe peut modifier les priorités de votre compte.
* Durée de la cible publicitaire.

   Le serveur de manifeste détecte la cible et la durée de la publicité dans la liste de lecture du contenu et l’envoie à CRS. L’Adobe peut modifier ce comportement afin que CRS utilise toujours une durée fixe que vous spécifiez pour votre compte.
