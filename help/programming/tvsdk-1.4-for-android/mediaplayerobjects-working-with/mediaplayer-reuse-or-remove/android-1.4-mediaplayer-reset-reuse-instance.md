---
description: Lorsque vous réinitialisez une instance MediaPlayer, elle revient à son état IDLE non initialisé tel que défini dans MediaPlayerState.
seo-description: Lorsque vous réinitialisez une instance MediaPlayer, elle revient à son état IDLE non initialisé tel que défini dans MediaPlayerState.
seo-title: Réinitialiser ou réutiliser une instance MediaPlayer
title: Réinitialiser ou réutiliser une instance MediaPlayer
uuid: 72cc4511-8ab0-44e5-b93c-b36f0321bba8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Réinitialiser, réutiliser ou supprimer une instance MediaPlayer {#reset-or-reuse-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

Lorsque vous réinitialisez une instance MediaPlayer, elle revient à son état IDLE non initialisé tel que défini dans MediaPlayerState.

Cette opération est utile dans les cas suivants :

* Vous souhaitez réutiliser une `MediaPlayer` instance mais devez charger une nouvelle `MediaResource` (contenu vidéo) et remplacer l’instance précédente.

   La réinitialisation vous permet de réutiliser l’ `MediaPlayer` instance sans avoir à libérer des ressources, recréer les ressources `MediaPlayer`et les réaffecter.

* Lorsque l’état `MediaPlayer` est ERREUR et doit être effacé.

   >[!IMPORTANT]
   >
   >C&#39;est le seul moyen de récupérer de l&#39;état ERROR.

1. Appelez `reset` à rétablir l’état non initialisé de l’ `MediaPlayer` instance :

   ```java
   void reset() throws IllegalStateException; 
   ```

1. Utilisez `MediaPlayer.replaceCurrentResource` pour charger un autre `MediaResource`.

   >[!TIP]
   >
   >Pour effacer une erreur, chargez la même `MediaResource`.

1. Lorsque vous recevez le rappel `STATUS_CHANGED` avec l’état PRÉPARÉ,  la lecture.

## Publication d’une instance et de ressources MediaPlayer{#release-a-mediaplayer-instance-and-resources}

Vous devez libérer une instance et des ressources MediaPlayer lorsque vous n’avez plus besoin de MediaResource.

Lorsque vous relâchez un `MediaPlayer` objet, les ressources matérielles sous-jacentes associées à cet `MediaPlayer` objet sont réparties.

Voici quelques raisons de publier un MediaPlayer :

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Le fait de laisser un `MediaPlayer` objet inutile peut entraîner une consommation continue de batterie pour les périphériques mobiles.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un périphérique, une erreur de lecture peut se produire pour d’autres applications.

1. Relâchez le `MediaPlayer`.

   ```java
   void release() throws IllegalStateException;
   ```

Une fois l’ `MediaPlayer` instance libérée, vous ne pouvez plus l’utiliser. Si une méthode de l’ `MediaPlayer` interface est appelée une fois qu’elle est relâchée, une `IllegalStateException` méthode est lancée.