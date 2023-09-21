---
description: TVSDK distribue des événements d’élément du lecteur multimédia en réponse au chargement d’un élément multimédia.
title: Événements Loader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Événements Loader{#loader-events}

TVSDK distribue des événements d’élément du lecteur multimédia en réponse au chargement d’un élément multimédia.

Ces événements fournissent un autre workflow. Vous n’êtes pas tenu de mettre en oeuvre cette interface lors de la création d’une `MediaPlayer`. Utilisez-le lorsque vous souhaitez qu’une `MediaPlayerItemLoader`.

Pour être averti des événements liés au chargement d’une ressource de lecteur multimédia, enregistrez les écouteurs des événements suivants avec la variable `MediaPlayerItemLoader` .

| Événement | Signification |
|---|---|
| MediaPlayerItemLoader.[terminé](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | Chargement de la ressource multimédia terminé avec succès. |
| MediaPlayerItemLoader.[failed](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | Un problème s’est produit lors du chargement des ressources multimédia. |
