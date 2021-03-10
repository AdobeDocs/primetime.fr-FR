---
description: Vous devez libérer une instance et des ressources MediaPlayer lorsque vous n’avez plus besoin de MediaResource.
title: Publication d’une instance et de ressources MediaPlayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '120'
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