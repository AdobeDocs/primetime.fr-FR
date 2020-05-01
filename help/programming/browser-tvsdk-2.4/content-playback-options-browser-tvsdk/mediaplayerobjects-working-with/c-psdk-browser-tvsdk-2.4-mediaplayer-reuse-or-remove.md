---
description: Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.
seo-description: Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.
seo-title: Réutilisation ou suppression d’une instance MediaPlayer
title: Réutilisation ou suppression d’une instance MediaPlayer
uuid: 0b9a06b0-ece7-4e18-9221-a4528bcbc141
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Réutilisation ou suppression d’une instance MediaPlayer{#reuse-or-remove-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

## Réinitialisation ou réutilisation d’une instance MediaPlayer {#section_C183E6164C184C3CBC5321FC6A2528EA}

Vous pouvez réinitialiser une `MediaPlayer` instance pour la rétablir à son état IDLE non initialisé, comme défini dans `MediaPlayerStatus`. Vous pouvez également remplacer l&#39;élément multimédia actif ou en définir un nouveau à l&#39;aide d&#39;une ressource multimédia précédemment chargée.

Cette opération est utile dans les cas suivants :

* Vous souhaitez réutiliser une `MediaPlayer` instance mais devez charger une nouvelle `MediaResource` (contenu vidéo) et remplacer l’instance précédente.

   La réinitialisation vous permet de réutiliser l’ `MediaPlayer` instance sans avoir à débloquer les ressources, recréer les `MediaPlayer`ressources et les réaffecter. La `replaceCurrentItem` méthode effectue automatiquement ces étapes pour vous.

* Lorsque la `MediaPlayer` variable est dans un état ERREUR et doit être effacée.

   >[!IMPORTANT]
   >
   >C&#39;est le seul moyen de récupérer de l&#39;état ERROR.

1. Appelez `MediaPlayer.reset()` pour rétablir l&#39;état non initialisé de l&#39; `MediaPlayer` instance :

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. Appel `MediaPlayer.replaceCurrentItem()` pour charger un autre `MediaResource`

   >[!TIP]
   >
   >Pour effacer une erreur, chargez la même `MediaResource`.

1. Appelez la `prepareToPlay()` méthode.

   >[!NOTE]
   >
   >Lorsque vous recevez le `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` événement avec l’état PRÉPARÉ, vous pouvez début la lecture.

## Publication d’une instance et de ressources MediaPlayer {#section_2D159975C82245098E7078FE0B1578CE}

Vous devez libérer une `MediaPlayer` instance et des ressources lorsque vous n’avez plus besoin de MediaResource.

Voici quelques raisons de publier un `MediaPlayer`:

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Le fait de laisser un `MediaPlayer` objet inutile peut entraîner une consommation continue de batterie pour les périphériques mobiles.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un périphérique, une erreur de lecture peut se produire pour d’autres applications.

* Relâchez le `MediaPlayer`.

   ```js
   void release()
   ```

   >[!NOTE]
   >
   >Une fois l’ `MediaPlayer` instance libérée, vous ne pouvez plus l’utiliser. Si une méthode de l’ `MediaPlayer` interface est appelée après sa publication, une `IllegalStateException` est générée.

