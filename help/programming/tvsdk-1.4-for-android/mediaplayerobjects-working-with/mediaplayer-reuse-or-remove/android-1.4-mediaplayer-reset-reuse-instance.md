---
description: Lorsque vous réinitialisez une instance MediaPlayer, elle revient à son état IDLE non initialisé tel que défini dans MediaPlayerState.
title: Réinitialisation ou réutilisation d’une instance MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Réinitialiser, réutiliser ou supprimer une instance MediaPlayer {#reset-or-reuse-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

Lorsque vous réinitialisez une instance MediaPlayer, elle revient à son état IDLE non initialisé tel que défini dans MediaPlayerState.

Cette opération est utile dans les cas suivants :

* Vous souhaitez réutiliser une `MediaPlayer` mais doit charger une nouvelle instance `MediaResource` (contenu vidéo) et remplacez l’instance précédente.

  La réinitialisation vous permet de réutiliser le `MediaPlayer` sans avoir à libérer des ressources, recréant la variable `MediaPlayer`et réaffecter les ressources.

* Lorsque la variable `MediaPlayer` se trouve à l’état ERROR et doit être effacé.

  >[!IMPORTANT]
  >
  >Il s’agit de la seule façon de récupérer de l’état ERROR.

1. Appeler `reset` pour renvoyer la variable `MediaPlayer` à son état non initialisé :

   ```java
   void reset() throws IllegalStateException; 
   ```

1. Utilisation `MediaPlayer.replaceCurrentResource` pour charger un autre `MediaResource`.

   >[!TIP]
   >
   >Pour effacer une erreur, chargez la même `MediaResource`.

1. Lorsque vous recevez la variable `STATUS_CHANGED` rappel d’événement avec l’état PREPARED , démarrez la lecture.

## Publication d’une instance et de ressources MediaPlayer{#release-a-mediaplayer-instance-and-resources}

Vous devez publier une instance et des ressources MediaPlayer lorsque vous n’avez plus besoin de MediaResource.

Lorsque vous lancez une `MediaPlayer` , les ressources matérielles sous-jacentes associées à cet objet `MediaPlayer` sont désaffectés.

Voici quelques raisons de publier un MediaPlayer :

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Laisser un objet inutile `MediaPlayer` peut entraîner une consommation continue de la batterie pour les appareils mobiles.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un appareil, l’échec de lecture peut se produire pour d’autres applications.

1. Publiez la `MediaPlayer`.

   ```java
   void release() throws IllegalStateException;
   ```

Après la `MediaPlayer` est publiée, vous ne pouvez plus l’utiliser. Si une méthode de la variable `MediaPlayer` une fois publiée, une `IllegalStateException` est généré.
