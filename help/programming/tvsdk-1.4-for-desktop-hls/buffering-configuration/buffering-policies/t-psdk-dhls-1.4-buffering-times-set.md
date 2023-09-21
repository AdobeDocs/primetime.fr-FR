---
description: MediaPlayer fournit des méthodes pour définir et obtenir l’heure de mise en mémoire tampon initiale et l’heure de mise en mémoire tampon de la lecture.
title: Définition des heures de mise en mémoire tampon
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Définition des heures de mise en mémoire tampon{#set-buffering-times}

MediaPlayer fournit des méthodes pour définir et obtenir l’heure de mise en mémoire tampon initiale et l’heure de mise en mémoire tampon de la lecture.

>[!TIP]
>
>Si vous ne définissez pas les paramètres de contrôle de la mémoire tampon avant de commencer la lecture, le lecteur multimédia met par défaut 2 secondes pour la mémoire tampon initiale et 30 secondes pour la durée de la mémoire tampon de lecture en cours.

1. Configurez la variable `BufferControlParameters` qui encapsule les paramètres initiaux de durée de la mémoire tampon et de durée de la lecture :

       Cette classe fournit les méthodes d’usine suivantes :
   
   * Pour définir la durée initiale de la mémoire tampon sur celle de la lecture :

     ```
     createSimple(bufferTime:uint):BufferControlParameters
     ```

   * Pour définir les heures de mémoire tampon initiales et de lecture :

     ```
     createDual(initialBufferTime:uint, playbackBufferTime:uint):BufferControlParameters 
     ```

     Ces méthodes renvoient une `IllegalArgumentException` si les paramètres ne sont pas valides, par exemple :

   * La durée initiale de la mémoire tampon est inférieure à zéro.
   * Le temps de mémoire tampon initial est supérieur au temps de mémoire tampon.

1. Pour définir les valeurs des paramètres de mémoire tampon, utilisez cette méthode. `MediaPlayer` method :

   ```
   public function set bufferControlParameters(value:BufferControlParameters):void
   ```

1. Pour obtenir les valeurs actuelles du paramètre de mémoire tampon, utilisez cette méthode. `MediaPlayer` method :

   ```
   public function get bufferControlParameters():BufferControlParameters
   ```

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

Par exemple, pour définir la mémoire tampon initiale sur 2 secondes et la durée de la mémoire tampon de lecture sur 30 secondes :

```
mediaPlayer.bufferControlParameters = BufferControlParameters.createDual(2000, 30000); 
```

La variable `psdkdemo` démontre cette fonctionnalité ; utilisez les paramètres de l’application pour définir les valeurs de mémoire tampon.
