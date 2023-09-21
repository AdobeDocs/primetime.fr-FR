---
description: Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.
title: Réutilisation ou suppression d’une instance MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Réutilisation ou suppression d’une instance MediaPlayer{#reuse-or-remove-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

## Réinitialisation ou réutilisation d’une instance MediaPlayer {#section_C183E6164C184C3CBC5321FC6A2528EA}

Vous pouvez réinitialiser une `MediaPlayer` pour la renvoyer à son état IDLE non initialisé tel que défini dans `MediaPlayerStatus`. Vous pouvez également remplacer l’élément multimédia actuel ou en définir un nouveau à l’aide d’une ressource multimédia précédemment chargée.

Cette opération est utile dans les cas suivants :

* Vous souhaitez réutiliser une `MediaPlayer` mais doit charger une nouvelle instance `MediaResource` (contenu vidéo) et remplacez l’instance précédente.

  La réinitialisation vous permet de réutiliser le `MediaPlayer` sans avoir à libérer des ressources, recréant la variable `MediaPlayer`et réaffecter les ressources. La variable `replaceCurrentItem` effectue automatiquement cette procédure.

* Lorsque la variable `MediaPlayer` se trouve à l’état ERROR et doit être effacé.

  >[!IMPORTANT]
  >
  >Il s’agit de la seule façon de récupérer de l’état ERROR.

1. Appeler `MediaPlayer.reset()` pour renvoyer la variable `MediaPlayer` à son état non initialisé :

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. Appeler `MediaPlayer.replaceCurrentItem()` pour charger un autre `MediaResource`

   >[!TIP]
   >
   >Pour effacer une erreur, chargez la même `MediaResource`.

1. Appelez le `prepareToPlay()` .

   >[!NOTE]
   >
   >Lorsque vous recevez la variable `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` avec l’état PRÉPARÉ , vous pouvez démarrer la lecture.

## Publication d’une instance et de ressources MediaPlayer {#section_2D159975C82245098E7078FE0B1578CE}

Vous devez publier une `MediaPlayer` instance et ressources lorsque vous n’avez plus besoin de MediaResource.

Voici quelques raisons de publier une `MediaPlayer`:

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Laisser un objet inutile `MediaPlayer` peut entraîner une consommation continue de la batterie pour les appareils mobiles.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un appareil, l’échec de lecture peut se produire pour d’autres applications.

* Publiez la `MediaPlayer`.

  ```js
  void release()
  ```

  >[!NOTE]
  >
  >Après la `MediaPlayer` est publiée, vous ne pouvez plus l’utiliser. Si une méthode de la variable `MediaPlayer` une fois publiée, une `IllegalStateException` est généré.
