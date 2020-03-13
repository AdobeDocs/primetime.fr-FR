---
description: TVSDK distribue des  d’éléments du lecteur multimédia en réponse au chargement d’un élément multimédia.
seo-description: TVSDK distribue des  d’éléments du lecteur multimédia en réponse au chargement d’un élément multimédia.
seo-title: de chargement
title: de chargement
uuid: 1b401ff5-4313-4c64-8be9-99bdeb58ba2a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# de chargement{#loader-events}

TVSDK distribue des  d’éléments du lecteur multimédia en réponse au chargement d’un élément multimédia.

Ces  fournissent un autre flux de travail. Vous n’êtes pas tenu de mettre en oeuvre cette interface lors de la création d’un lecteur multimédia. Utilisez-le lorsque vous voulez avoir une `MediaPlayerItemLoader`.

Pour être averti des  liées au chargement d&#39;une ressource de lecteur multimédia, enregistrez une implémentation de `MediaPlayerItemLoader.LoaderListener` incluant le suivant .

| Event | Signification |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([mediaPlayerItem](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) playerItem) | Chargement de la ressource multimédia terminé. |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | Un problème est survenu lors du chargement des ressources du média. |

>[!NOTE]
>
>Voir aussi `onLoadInfo (loadInfo)` sous  QoS.

