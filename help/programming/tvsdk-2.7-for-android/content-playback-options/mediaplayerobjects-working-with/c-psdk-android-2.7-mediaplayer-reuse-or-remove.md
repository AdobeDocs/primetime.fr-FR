---
description: Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.
seo-description: Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.
seo-title: Réutilisation ou suppression d’une instance MediaPlayer
title: Réutilisation ou suppression d’une instance MediaPlayer
uuid: da7b3468-3f0f-4025-927b-d47764a053af
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Réutilisation ou suppression d’une instance MediaPlayer {#reuse-or-remove-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

## Réinitialiser ou réutiliser une instance MediaPlayer {#section_E6A2446A2D0B4ACD9EA980685B2E57D9}

Lorsque vous réinitialisez une `MediaPlayer` instance, elle revient à son état IDLE non initialisé, tel que défini dans `MediaPlayerStatus`

* Vous souhaitez réutiliser une `MediaPlayer` instance mais devez charger une nouvelle `MediaResource` (contenu vidéo) et remplacer l’instance précédente.

   La réinitialisation vous permet de réutiliser l’ `MediaPlayer` instance sans avoir à libérer des ressources, recréer les ressources `MediaPlayer`et les réaffecter.

* Lorsque l’état `MediaPlayer` est ERREUR et doit être effacé.

   >[!IMPORTANT]
   >
   >C&#39;est la seule façon de récupérer de l&#39;état ERROR.

   1. Appelez `reset` à rétablir l’état non initialisé de l’ `MediaPlayer` instance :

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. Utilisez `MediaPlayer.replaceCurrentResource()` pour charger un autre `MediaResource`.

      >[!NOTE]
      >
      >Pour effacer une erreur, chargez la même `MediaResource`.

   1. Lorsque vous recevez le rappel `STATUS_CHANGED` avec `PREPARED` l’état,  la lecture.

## Publication d’une instance et de ressources MediaPlayer {#section_13A0914AFF784943ABC343F7EB249C4E}

Vous devez libérer une `MediaPlayer` instance et des ressources lorsque vous n’avez plus besoin de la `MediaResource`.

Lorsque vous relâchez un `MediaPlayer` objet, les ressources matérielles sous-jacentes associées à cet `MediaPlayer` objet sont réparties.

Voici quelques raisons de publier une `MediaPlayer`:

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Le fait de laisser un `MediaPlayer` objet instancié inutile peut entraîner une consommation continue de batterie pour les périphériques mobiles.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un périphérique, une erreur de lecture peut se produire pour d’autres applications.

* Relâchez le `MediaPlayer`.

   ```java
   void release() throws MediaPlayerException;
   ```

   >[!NOTE]
   >
   >Une fois l’ `MediaPlayer` instance libérée, vous ne pouvez plus l’utiliser. Si une méthode de l’ `MediaPlayer` interface est appelée une fois qu’elle a été libérée, une `MediaPlayerException` est générée.