---
description: Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.
seo-description: Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.
seo-title: Réutilisation ou suppression d’une instance MediaPlayer
title: Réutilisation ou suppression d’une instance MediaPlayer
uuid: 0b9a06b0-ece7-4e18-9221-a4528bcbc141
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# Réutilisation ou suppression d’une instance MediaPlayer{#reuse-or-remove-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

## Réinitialiser ou réutiliser une instance MediaPlayer {#section_C183E6164C184C3CBC5321FC6A2528EA}

Vous pouvez réinitialiser une instance `MediaPlayer` pour la rendre à son état IDLE non initialisé tel que défini dans `MediaPlayerStatus`. Vous pouvez également remplacer l&#39;élément multimédia actif ou en définir un nouveau à l&#39;aide d&#39;une ressource multimédia précédemment chargée.

Cette opération est utile dans les cas suivants :

* Vous souhaitez réutiliser une instance `MediaPlayer` mais devez charger une nouvelle instance `MediaResource` (contenu vidéo) et remplacer l’instance précédente.

   La réinitialisation vous permet de réutiliser l&#39;instance `MediaPlayer` sans avoir à libérer des ressources, recréer `MediaPlayer` et réaffecter des ressources. La méthode `replaceCurrentItem` effectue automatiquement ces étapes pour vous.

* Lorsque l&#39;état `MediaPlayer` est ERROR et doit être effacé.

   >[!IMPORTANT]
   >
   >C&#39;est le seul moyen de récupérer de l&#39;état ERROR.

1. Appelez `MediaPlayer.reset()` pour renvoyer l&#39;instance `MediaPlayer` à son état non initialisé :

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. Appeler `MediaPlayer.replaceCurrentItem()` pour charger un autre `MediaResource`

   >[!TIP]
   >
   >Pour effacer une erreur, chargez le même `MediaResource`.

1. Appelez la méthode `prepareToPlay()`.

   >[!NOTE]
   >
   >Lorsque vous recevez le événement `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` avec l’état PRÉPARÉ, vous pouvez début la lecture.

## Publication d’une instance et de ressources MediaPlayer {#section_2D159975C82245098E7078FE0B1578CE}

Vous devez libérer une instance et des ressources `MediaPlayer` lorsque vous n’avez plus besoin de MediaResource.

Voici quelques raisons de publier un `MediaPlayer` :

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Le fait de laisser un objet `MediaPlayer` inutile peut entraîner une consommation continue de batterie pour les périphériques mobiles.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un périphérique, une erreur de lecture peut se produire pour d’autres applications.

* Libérez le `MediaPlayer`.

   ```js
   void release()
   ```

   >[!NOTE]
   >
   >Une fois l&#39;instance `MediaPlayer` libérée, vous ne pouvez plus l&#39;utiliser. Si une méthode de l&#39;interface `MediaPlayer` est appelée après sa publication, un `IllegalStateException` est généré.

