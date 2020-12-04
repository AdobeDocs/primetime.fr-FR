---
description: Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.
seo-description: Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.
seo-title: Réutilisation ou suppression d’une instance MediaPlayer
title: Réutilisation ou suppression d’une instance MediaPlayer
uuid: da7b3468-3f0f-4025-927b-d47764a053af
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---


# Réutilisation ou suppression d’une instance MediaPlayer {#reuse-or-remove-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

## Réinitialiser ou réutiliser une instance MediaPlayer {#section_E6A2446A2D0B4ACD9EA980685B2E57D9}

Lorsque vous réinitialisez une instance `MediaPlayer`, elle revient à son état IDLE non initialisé, tel que défini dans `MediaPlayerStatus`

* Vous souhaitez réutiliser une instance `MediaPlayer` mais devez charger une nouvelle instance `MediaResource` (contenu vidéo) et remplacer l’instance précédente.

   La réinitialisation vous permet de réutiliser l&#39;instance `MediaPlayer` sans avoir à libérer des ressources, recréer `MediaPlayer` et réaffecter des ressources.

* Lorsque le `MediaPlayer` est en état ERROR et doit être effacé.

   >[!IMPORTANT]
   >
   >C&#39;est le seul moyen de récupérer de l&#39;état ERROR.

   1. Appelez `reset` pour renvoyer l&#39;instance `MediaPlayer` à son état non initialisé :

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. Utilisez `MediaPlayer.replaceCurrentResource()` pour charger un autre `MediaResource`.

      >[!NOTE]
      >
      >Pour effacer une erreur, chargez le même `MediaResource`.

   1. Lorsque vous recevez le rappel de événement `STATUS_CHANGED` avec l’état `PREPARED`, début la lecture.

## Publication d’une instance et de ressources MediaPlayer {#section_13A0914AFF784943ABC343F7EB249C4E}

Vous devez libérer une instance et des ressources `MediaPlayer` lorsque vous n&#39;avez plus besoin de `MediaResource`.

Lorsque vous relâchez un objet `MediaPlayer`, les ressources matérielles sous-jacentes associées à cet objet `MediaPlayer` sont cédées.

Voici quelques raisons de publier un `MediaPlayer` :

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Le fait de laisser un objet `MediaPlayer` instancié inutile peut entraîner une consommation continue de batterie pour les périphériques mobiles.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un périphérique, une erreur de lecture peut se produire pour d’autres applications.

* Libérez le `MediaPlayer`.

   ```java
   void release() throws MediaPlayerException;
   ```

   >[!NOTE]
   >
   >Une fois l&#39;instance `MediaPlayer` libérée, vous ne pouvez plus l&#39;utiliser. Si une méthode de l&#39;interface `MediaPlayer` est appelée après sa publication, un `MediaPlayerException` est généré.