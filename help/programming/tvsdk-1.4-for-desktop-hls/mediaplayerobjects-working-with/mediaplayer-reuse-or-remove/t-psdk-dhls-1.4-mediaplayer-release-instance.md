---
description: Vous devez libérer une instance et des ressources MediaPlayer lorsque vous n’avez plus besoin de MediaResource.
seo-description: Vous devez libérer une instance et des ressources MediaPlayer lorsque vous n’avez plus besoin de MediaResource.
seo-title: Publication d’une instance et de ressources MediaPlayer
title: Publication d’une instance et de ressources MediaPlayer
uuid: e7b2112e-8add-4789-9345-5f829d39d639
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Publication d’une instance et de ressources MediaPlayer{#release-a-mediaplayer-instance-and-resources}

Vous devez libérer une instance et des ressources MediaPlayer lorsque vous n’avez plus besoin de MediaResource.

Lorsque vous relâchez un objet `MediaPlayer`, les ressources matérielles sous-jacentes associées à cet objet `MediaPlayer` sont cédées.

Voici quelques raisons de publier un `MediaPlayer` :

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un périphérique, une erreur de lecture peut se produire pour d’autres applications.

1. Libérez le `MediaPlayer`.

   ```
   function release():void;
   ```

Une fois l&#39;instance `MediaPlayer` libérée, vous ne pouvez plus l&#39;utiliser. Si une méthode de l&#39;interface `MediaPlayer` est appelée après sa publication, un `IllegalStateException` est généré.