---
description: TVSDK distribue des événements d’éléments du lecteur multimédia en réponse au chargement d’un élément multimédia.
title: Événements de chargement
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# Événements de chargement{#loader-events}

TVSDK distribue des événements d’éléments du lecteur multimédia en réponse au chargement d’un élément multimédia.

Ces événements offrent un autre processus. Vous n’êtes pas tenu de mettre en oeuvre cette interface lors de la création d’un MediaPlayer. Utilisez cette option lorsque vous souhaitez avoir un `MediaPlayerItemLoader`.

Pour être averti des événements liés au chargement d&#39;une ressource de lecteur multimédia, enregistrez une implémentation de `MediaPlayerItemLoader.LoaderListener` incluant les événements suivants.

| Événement | Signification |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) mediaPlayerItemplayerItem) | Chargement de la ressource multimédia terminé. |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | Un problème est survenu lors du chargement des ressources du média. |

>[!NOTE]
>
>Voir aussi `onLoadInfo (loadInfo)` sous événements QoS.

