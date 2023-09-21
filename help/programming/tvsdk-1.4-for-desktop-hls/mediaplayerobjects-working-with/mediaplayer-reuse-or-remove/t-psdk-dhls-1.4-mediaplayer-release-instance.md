---
description: Vous devez publier une instance et des ressources MediaPlayer lorsque vous n’avez plus besoin de MediaResource.
title: Publication d’une instance et de ressources MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# Publication d’une instance et de ressources MediaPlayer{#release-a-mediaplayer-instance-and-resources}

Vous devez publier une instance et des ressources MediaPlayer lorsque vous n’avez plus besoin de MediaResource.

Lorsque vous lancez une `MediaPlayer` , les ressources matérielles sous-jacentes associées à cet objet `MediaPlayer` sont désaffectés.

Voici quelques raisons de publier une `MediaPlayer`:

* Le fait de détenir des ressources inutiles peut affecter les performances.
* Si plusieurs instances du même codec vidéo ne sont pas prises en charge sur un appareil, l’échec de lecture peut se produire pour d’autres applications.

1. Publiez la `MediaPlayer`.

   ```
   function release():void;
   ```

Après la `MediaPlayer` est publiée, vous ne pouvez plus l’utiliser. Si une méthode de la variable `MediaPlayer` une fois publiée, une `IllegalStateException` est généré.
