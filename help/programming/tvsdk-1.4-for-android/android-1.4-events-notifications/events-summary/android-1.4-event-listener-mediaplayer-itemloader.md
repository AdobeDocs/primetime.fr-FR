---
description: TVSDK distribue des événements d’élément du lecteur multimédia en réponse au chargement d’un élément multimédia.
title: Événements Loader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# Événements Loader{#loader-events}

TVSDK distribue des événements d’élément du lecteur multimédia en réponse au chargement d’un élément multimédia.

Ces événements fournissent un autre workflow. Vous n’êtes pas tenu de mettre en oeuvre cette interface lors de la création d’un lecteur multimédia. Utilisez-le lorsque vous souhaitez qu’une `MediaPlayerItemLoader`.

Pour être averti des événements liés au chargement d’une ressource de lecteur multimédia, enregistrez une mise en oeuvre de `MediaPlayerItemLoader.LoaderListener` y compris les événements suivants.

| Événement | Signification |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([mediaPlayerItem](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) playerItem) | Chargement de la ressource multimédia terminé avec succès. |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | Un problème s’est produit lors du chargement des ressources multimédia. |

>[!NOTE]
>
>Voir aussi `onLoadInfo (loadInfo)` sous les événements QoS.
