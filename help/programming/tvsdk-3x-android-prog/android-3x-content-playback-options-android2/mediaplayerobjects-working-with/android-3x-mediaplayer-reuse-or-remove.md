---
description: Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.
title: Réutilisation ou suppression d’une instance MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Réutilisation ou suppression d’une instance MediaPlayer {#reuse-or-remove-a-mediaplayer-instance}

Vous pouvez réinitialiser, réutiliser ou libérer une instance MediaPlayer dont vous n’avez plus besoin.

## Réinitialisation ou réutilisation d’une instance MediaPlayer {#section_E6A2446A2D0B4ACD9EA980685B2E57D9}

Lorsque vous réinitialisez une `MediaPlayer` l’instance, elle revient à son état IDLE non initialisé tel que défini dans `MediaPlayerStatus`.

Cette opération est utile dans les cas suivants :

* Vous souhaitez réutiliser une `MediaPlayer` mais doit charger une nouvelle instance `MediaResource` (contenu vidéo) et remplacez l’instance précédente.

  La réinitialisation vous permet de réutiliser le `MediaPlayer` sans avoir à libérer des ressources, recréant la variable `MediaPlayer`et réaffecter les ressources.

* Lorsque la variable `MediaPlayer` est à l’état ERROR et doit être effacé.

  >[!IMPORTANT]
  >
  >C&#39;est la seule façon de récupérer du statut ERREUR.

   1. Appeler `reset` pour renvoyer la variable `MediaPlayer` à son état non initialisé :

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. Utilisation `MediaPlayer.replaceCurrentResource()` pour charger un autre `MediaResource`.

      >[!NOTE]
      >
      >Pour effacer une erreur, chargez la même `MediaResource`.

   1. Lorsque vous recevez la variable `STATUS_CHANGED` rappel d’événement avec `PREPARED` , démarrez la lecture.

## Publication d’une instance et de ressources MediaPlayer {#section_13A0914AFF784943ABC343F7EB249C4E}

Vous devez publier une `MediaPlayer` instance et ressources lorsque vous n’avez plus besoin de la fonction `MediaResource`.

Lorsque vous lancez une `MediaPlayer` , les ressources matérielles sous-jacentes associées à cet objet `MediaPlayer` sont désaffectés.

Voici quelques raisons de publier une `MediaPlayer`:

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Laisser un objet inutile `MediaPlayer` instancié peut entraîner une consommation continue de la batterie pour les appareils mobiles.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un appareil, l’échec de lecture peut se produire pour d’autres applications.

* Publiez la `MediaPlayer`.

  ```java
  void release() throws MediaPlayerException;
  ```

  >[!NOTE]
  >
  >Après la `MediaPlayer` est publiée, vous ne pouvez plus l’utiliser. Si une méthode de la variable `MediaPlayer` est appelée une fois qu’elle est publiée, une `MediaPlayerException` est généré.
