---
description: TVSDK distribue des événements d’éléments du lecteur multimédia en réponse au chargement d’un élément multimédia.
seo-description: TVSDK distribue des événements d’éléments du lecteur multimédia en réponse au chargement d’un élément multimédia.
seo-title: événements de chargement
title: événements de chargement
uuid: 1b401ff5-4313-4c64-8be9-99bdeb58ba2a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# événements de chargement{#loader-events}

TVSDK distribue des événements d’éléments du lecteur multimédia en réponse au chargement d’un élément multimédia.

Ces événements offrent un autre processus. Vous n’êtes pas tenu de mettre en oeuvre cette interface lors de la création d’un MediaPlayer. Utilisez-le lorsque vous voulez avoir un `MediaPlayerItemLoader`.

Pour être informé des événements liés au chargement d&#39;une ressource de lecteur multimédia, enregistrez une mise en oeuvre de `MediaPlayerItemLoader.LoaderListener` incluant les événements suivants.

| Événement | Signification |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([mediaPlayerItem player](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) Item) | Chargement de la ressource multimédia terminé. |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | Un problème est survenu lors du chargement des ressources du média. |

>[!NOTE]
>
>Voir aussi `onLoadInfo (loadInfo)` sous événements QoS.

