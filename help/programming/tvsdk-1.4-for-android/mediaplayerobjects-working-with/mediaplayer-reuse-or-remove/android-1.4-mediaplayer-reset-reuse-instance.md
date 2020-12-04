---
description: Lorsque vous réinitialisez une instance MediaPlayer, elle est renvoyée à son état IDLE non initialisé tel que défini dans MediaPlayerState.
seo-description: Lorsque vous réinitialisez une instance MediaPlayer, elle est renvoyée à son état IDLE non initialisé tel que défini dans MediaPlayerState.
seo-title: Réinitialisation ou réutilisation d’une instance MediaPlayer
title: Réinitialisation ou réutilisation d’une instance MediaPlayer
uuid: 72cc4511-8ab0-44e5-b93c-b36f0321bba8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# Réinitialiser, réutiliser ou supprimer une instance MediaPlayer {#reset-or-reuse-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

Lorsque vous réinitialisez une instance MediaPlayer, elle est renvoyée à son état IDLE non initialisé tel que défini dans MediaPlayerState.

Cette opération est utile dans les cas suivants :

* Vous souhaitez réutiliser une instance `MediaPlayer` mais devez charger une nouvelle instance `MediaResource` (contenu vidéo) et remplacer l’instance précédente.

   La réinitialisation vous permet de réutiliser l&#39;instance `MediaPlayer` sans avoir à libérer des ressources, recréer `MediaPlayer` et réaffecter des ressources.

* Lorsque l&#39;état `MediaPlayer` est ERROR et doit être effacé.

   >[!IMPORTANT]
   >
   >C&#39;est le seul moyen de récupérer de l&#39;état ERROR.

1. Appelez `reset` pour renvoyer l&#39;instance `MediaPlayer` à son état non initialisé :

   ```java
   void reset() throws IllegalStateException; 
   ```

1. Utilisez `MediaPlayer.replaceCurrentResource` pour charger un autre `MediaResource`.

   >[!TIP]
   >
   >Pour effacer une erreur, chargez le même `MediaResource`.

1. Lorsque vous recevez le rappel de événement `STATUS_CHANGED` avec l’état PRÉPARÉ, début la lecture.

## Publication d’une instance et de ressources MediaPlayer{#release-a-mediaplayer-instance-and-resources}

Vous devez libérer une instance et des ressources MediaPlayer lorsque vous n’avez plus besoin de MediaResource.

Lorsque vous relâchez un objet `MediaPlayer`, les ressources matérielles sous-jacentes associées à cet objet `MediaPlayer` sont cédées.

Voici quelques raisons de publier un MediaPlayer :

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Le fait de laisser un objet `MediaPlayer` inutile peut entraîner une consommation continue de batterie pour les périphériques mobiles.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un périphérique, une erreur de lecture peut se produire pour d’autres applications.

1. Libérez le `MediaPlayer`.

   ```java
   void release() throws IllegalStateException;
   ```

Une fois l&#39;instance `MediaPlayer` libérée, vous ne pouvez plus l&#39;utiliser. Si une méthode de l&#39;interface `MediaPlayer` est appelée après sa publication, un `IllegalStateException` est généré.