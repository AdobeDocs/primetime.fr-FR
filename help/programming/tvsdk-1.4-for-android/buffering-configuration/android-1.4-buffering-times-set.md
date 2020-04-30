---
description: Pour une visualisation plus fluide, TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.
seo-description: Pour une visualisation plus fluide, TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.
seo-title: Définition des heures de mise en mémoire tampon
title: Définition des heures de mise en mémoire tampon
uuid: 5a3945a4-1935-4797-b19d-84989850a487
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mise en mémoire tampon {#buffering}

Pour une visualisation plus fluide, TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.

TVSDK définit une durée de mémoire tampon de lecture d’au moins 30 secondes et une durée initiale de mémoire tampon d’au moins 2 secondes avant le début de lecture du média. Après les appels de l’application `play` mais avant le début de la lecture, TVSDK met le média en mémoire tampon jusqu’à la mise en mémoire tampon initiale afin d’offrir un début fluide lorsqu’il début effectivement la lecture.

Vous pouvez modifier les temps de mise en mémoire tampon en définissant de nouvelles stratégies de mise en mémoire tampon et vous pouvez modifier le moment où la mise en mémoire tampon initiale se produit en utilisant la fonction de mise en mémoire tampon instantanée.

## Définition des heures de mise en mémoire tampon {#set-buffering-times}

Le `MediaPlayer` fournit des méthodes pour définir et obtenir la mise en mémoire tampon initiale et la mise en mémoire tampon de la lecture.

>[!TIP]
>
>Si vous ne définissez pas les paramètres de contrôle de la mémoire tampon avant de commencer la lecture, le lecteur multimédia prend par défaut 2 secondes pour la mémoire tampon initiale et 30 secondes pour la durée de la mémoire tampon de lecture en cours.

1. Configurez l’ `BufferControlParameters` objet, qui encapsule les paramètres de contrôle de la durée de la mémoire tampon initiale et de la durée de la mémoire tampon de lecture :

       Cette classe fournit deux méthodes de fabrication :
   
   * Pour définir la durée initiale de la mémoire tampon sur celle de la lecture :

      ```java
      public static BufferControlParameters createSimple( 
          long bufferTime)
      ```

   * Pour définir à la fois les heures de mémoire tampon initiale et de lecture :

      ```java
      public static BufferControlParameters createDual( 
          long initialBuffer,   
          long bufferTime)
      ```

      Ces méthodes lancent un `IllegalArgumentException` si les paramètres ne sont pas valides, par exemple quand :

   * Le temps de mémoire tampon initial est inférieur à zéro.
   * La durée initiale de la mémoire tampon est supérieure à la durée de la mémoire tampon.

1. Pour définir les valeurs des paramètres de mémoire tampon, utilisez cette `MediaPlayer` méthode :

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. Pour obtenir les valeurs des paramètres de mémoire tampon actuels, utilisez cette `MediaPlayer` méthode :

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

   Si l&#39;AVE ne parvient pas à définir les valeurs spécifiées, le lecteur de médias entre à l&#39; `ERROR` état avec le code d&#39;erreur `SET_BUFFER_PARAMETERS_ERROR`.

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

Par exemple, pour définir la mémoire tampon initiale sur 2 secondes et la durée de lecture sur 30 secondes :

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(2000, 30000));
```

L’implémentation de référence Primetime illustre cette fonctionnalité ; utilisez les paramètres de l&#39;application pour définir les valeurs de la mémoire tampon.