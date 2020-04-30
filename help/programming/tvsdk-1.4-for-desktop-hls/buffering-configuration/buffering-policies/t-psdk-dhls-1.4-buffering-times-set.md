---
description: MediaPlayer fournit des méthodes pour définir et obtenir la mise en mémoire tampon initiale et la mise en mémoire tampon de la lecture.
seo-description: MediaPlayer fournit des méthodes pour définir et obtenir la mise en mémoire tampon initiale et la mise en mémoire tampon de la lecture.
seo-title: Définition des heures de mise en mémoire tampon
title: Définition des heures de mise en mémoire tampon
uuid: 25142b01-5381-49c9-b89a-24c858faaf13
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Définition des heures de mise en mémoire tampon{#set-buffering-times}

MediaPlayer fournit des méthodes pour définir et obtenir la mise en mémoire tampon initiale et la mise en mémoire tampon de la lecture.

>[!TIP]
>
>Si vous ne définissez pas les paramètres de contrôle de la mémoire tampon avant de commencer la lecture, le lecteur multimédia prend par défaut 2 secondes pour la mémoire tampon initiale et 30 secondes pour la durée de la mémoire tampon de lecture en cours.

1. Configurez l’ `BufferControlParameters` objet, qui encapsule les paramètres de contrôle de la durée de la mémoire tampon initiale et de la durée de la mémoire tampon de lecture :

       Cette classe fournit les méthodes de fabrique suivantes :
   
   * Pour définir la durée initiale de la mémoire tampon sur celle de la lecture :

      ```
      createSimple(bufferTime:uint):BufferControlParameters
      ```

   * Pour définir à la fois les heures de mémoire tampon initiale et de lecture :

      ```
      createDual(initialBufferTime:uint, playbackBufferTime:uint):BufferControlParameters 
      ```

      Ces méthodes lancent un `IllegalArgumentException` si les paramètres ne sont pas valides, par exemple quand :

   * Le temps de mémoire tampon initial est inférieur à zéro.
   * La durée initiale de la mémoire tampon est supérieure à la durée de la mémoire tampon.

1. Pour définir les valeurs des paramètres de mémoire tampon, utilisez cette `MediaPlayer` méthode :

   ```
   public function set bufferControlParameters(value:BufferControlParameters):void
   ```

1. Pour obtenir les valeurs des paramètres de mémoire tampon actuels, utilisez cette `MediaPlayer` méthode :

   ```
   public function get bufferControlParameters():BufferControlParameters
   ```

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

Par exemple, pour définir la mémoire tampon initiale sur 2 secondes et la durée de lecture sur 30 secondes :

```
mediaPlayer.bufferControlParameters = BufferControlParameters.createDual(2000, 30000); 
```

Le `psdkdemo` montre cette fonctionnalité. utilisez les paramètres de l&#39;application pour définir les valeurs de la mémoire tampon.
