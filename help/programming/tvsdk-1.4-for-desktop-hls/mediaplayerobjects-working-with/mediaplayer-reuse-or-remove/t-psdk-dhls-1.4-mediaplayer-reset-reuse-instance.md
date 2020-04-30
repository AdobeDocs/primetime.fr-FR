---
description: Lorsque vous réinitialisez une instance MediaPlayer, elle est renvoyée à son état IDLE non initialisé tel que défini dans MediaPlayerStatus.
seo-description: Lorsque vous réinitialisez une instance MediaPlayer, elle est renvoyée à son état IDLE non initialisé tel que défini dans MediaPlayerStatus.
seo-title: Réinitialisation ou réutilisation d’une instance MediaPlayer
title: Réinitialisation ou réutilisation d’une instance MediaPlayer
uuid: b376096b-0aed-4ac2-96e5-e30a4eaf742e
translation-type: tm+mt
source-git-commit: c547002eb8946f8ccc5a79d0836f3f814e823b97

---


# Réinitialisation ou réutilisation d’une instance MediaPlayer{#reset-or-reuse-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

Lorsque vous réinitialisez une instance MediaPlayer, elle est renvoyée à son état IDLE non initialisé tel que défini dans MediaPlayerStatus.

Cette opération est utile dans les cas suivants :

* Vous souhaitez réutiliser une `MediaPlayer` instance mais devez charger une nouvelle `MediaResource` (contenu vidéo) et remplacer l’instance précédente.

   La réinitialisation vous permet de réutiliser l’ `MediaPlayer` instance sans avoir à débloquer les ressources, recréer les `MediaPlayer`ressources et les réaffecter. Les méthodes `replaceCurrentItem` et `replaceCurrentResource` effectuent automatiquement ces étapes pour vous, sans avoir à appeler la méthode reset.

* Lorsque l&#39;état `MediaPlayer` est ERROR et doit être effacé.

   >[!IMPORTANT]
   >
   >C&#39;est le seul moyen de récupérer de l&#39;état ERROR.

1. Appelez `reset` pour rétablir l&#39;état non initialisé de l&#39; `MediaPlayer` instance :

   ```
   function reset():void; 
   ```

1. Utilisez `MediaPlayer.replaceCurrentItem` ou `MediaPlayer.replaceCurrentResource` pour charger un autre `MediaResource`.

   >[!TIP]
   >
   >Pour effacer une erreur, chargez la même `MediaResource`.

1. Lorsque vous recevez le `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` rapport avec l’ `PREPARED` état, début la lecture.
