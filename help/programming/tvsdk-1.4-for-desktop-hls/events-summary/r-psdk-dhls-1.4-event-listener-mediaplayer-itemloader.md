---
description: TVSDK distribue des événements d’éléments du lecteur multimédia en réponse au chargement d’un élément multimédia.
title: Événements de chargement
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Événements de chargement{#loader-events}

TVSDK distribue des événements d’éléments du lecteur multimédia en réponse au chargement d’un élément multimédia.

Ces événements offrent un autre processus. Vous n&#39;êtes pas tenu d&#39;implémenter cette interface lors de la création d&#39;un `MediaPlayer`. Utilisez cette option lorsque vous souhaitez avoir un `MediaPlayerItemLoader`.

Pour être averti des événements liés au chargement d&#39;une ressource de lecteur multimédia, enregistrez les écouteurs des événements suivants avec l&#39;objet `MediaPlayerItemLoader`.

| Événement | Signification |
|---|---|
| MediaPlayerItemLoader.[terminé](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | Chargement de la ressource multimédia terminé. |
| MediaPlayerItemLoader.[échoué](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | Un problème est survenu lors du chargement des ressources du média. |