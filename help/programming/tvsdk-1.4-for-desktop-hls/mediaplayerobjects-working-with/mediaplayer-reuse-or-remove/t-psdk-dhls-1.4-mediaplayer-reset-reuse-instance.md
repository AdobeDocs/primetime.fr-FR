---
description: Lorsque vous réinitialisez une instance MediaPlayer, elle est renvoyée à son état IDLE non initialisé tel que défini dans MediaPlayerStatus.
title: Réinitialisation ou réutilisation d’une instance MediaPlayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---


# Réinitialiser ou réutiliser une instance MediaPlayer{#reset-or-reuse-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

Lorsque vous réinitialisez une instance MediaPlayer, elle est renvoyée à son état IDLE non initialisé tel que défini dans MediaPlayerStatus.

Cette opération est utile dans les cas suivants :

* Vous souhaitez réutiliser une instance `MediaPlayer` mais devez charger une nouvelle instance `MediaResource` (contenu vidéo) et remplacer l’instance précédente.

   La réinitialisation vous permet de réutiliser l&#39;instance `MediaPlayer` sans avoir à libérer des ressources, recréer `MediaPlayer` et réaffecter des ressources. Les méthodes `replaceCurrentItem` et `replaceCurrentResource` effectuent automatiquement ces étapes pour vous, sans avoir à appeler la méthode reset.

* Lorsque `MediaPlayer` a un état ERROR et doit être effacé.

   >[!IMPORTANT]
   >
   >C&#39;est le seul moyen de récupérer de l&#39;état ERROR.

1. Appelez `reset` pour renvoyer l&#39;instance `MediaPlayer` à son état non initialisé :

   ```
   function reset():void; 
   ```

1. Utilisez `MediaPlayer.replaceCurrentItem` ou `MediaPlayer.replaceCurrentResource` pour charger un autre `MediaResource`.

   >[!TIP]
   >
   >Pour effacer une erreur, chargez le même `MediaResource`.

1. Lorsque vous recevez le `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` avec l&#39;état `PREPARED`, début la lecture.
