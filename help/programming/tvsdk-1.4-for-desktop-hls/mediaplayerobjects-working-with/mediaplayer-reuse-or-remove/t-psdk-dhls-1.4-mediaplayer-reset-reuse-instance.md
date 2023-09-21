---
description: Lorsque vous réinitialisez une instance MediaPlayer, elle revient à son état IDLE non initialisé tel que défini dans MediaPlayerStatus.
title: Réinitialisation ou réutilisation d’une instance MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Réinitialisation ou réutilisation d’une instance MediaPlayer{#reset-or-reuse-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

Lorsque vous réinitialisez une instance MediaPlayer, elle revient à son état IDLE non initialisé tel que défini dans MediaPlayerStatus.

Cette opération est utile dans les cas suivants :

* Vous souhaitez réutiliser une `MediaPlayer` mais doit charger une nouvelle instance `MediaResource` (contenu vidéo) et remplacez l’instance précédente.

  La réinitialisation vous permet de réutiliser le `MediaPlayer` sans avoir à libérer des ressources, recréant la variable `MediaPlayer`et réaffecter les ressources. La variable `replaceCurrentItem` et `replaceCurrentResource` effectuent automatiquement ces étapes, sans avoir à appeler la méthode reset .

* Lorsque la variable `MediaPlayer` a le statut ERROR et doit être effacé.

  >[!IMPORTANT]
  >
  >C&#39;est la seule façon de récupérer du statut ERREUR.

1. Appeler `reset` pour renvoyer la variable `MediaPlayer` à son état non initialisé :

   ```
   function reset():void; 
   ```

1. Utilisation `MediaPlayer.replaceCurrentItem` ou `MediaPlayer.replaceCurrentResource` pour charger un autre `MediaResource`.

   >[!TIP]
   >
   >Pour effacer une erreur, chargez la même `MediaResource`.

1. Lorsque vous recevez la variable `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` avec la propriété `PREPARED` , démarrez la lecture.
