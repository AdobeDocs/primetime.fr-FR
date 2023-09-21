---
description: Pour offrir une expérience de visionnage plus fluide, TVSDK place parfois la vidéo en mémoire tampon. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.
title: Définition des heures de mise en mémoire tampon
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Mise en mémoire tampon {#buffering}

Pour offrir une expérience de visionnage plus fluide, TVSDK place parfois la vidéo en mémoire tampon. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.

TVSDK définit une durée de mémoire tampon de lecture d’au moins 30 secondes et une durée de mémoire tampon initiale d’au moins 2 secondes avant le début de la lecture du média. Après les appels de l’application `play` mais avant le début de la lecture, TVSDK met le média en mémoire tampon jusqu’à la date initiale pour offrir un démarrage fluide lorsqu’il commence réellement la lecture.

Vous pouvez modifier les temps de mise en mémoire tampon en définissant de nouvelles stratégies de mise en mémoire tampon et vous pouvez modifier le moment où la mise en mémoire tampon initiale se produit à l’aide de l’instantané.

## Définition des heures de mise en mémoire tampon {#set-buffering-times}

La variable `MediaPlayer` fournit des méthodes pour définir et obtenir l’heure de mise en mémoire tampon initiale et l’heure de mise en mémoire tampon de la lecture.

>[!TIP]
>
>Si vous ne définissez pas les paramètres de contrôle de la mémoire tampon avant de commencer la lecture, le lecteur multimédia met par défaut 2 secondes pour la mémoire tampon initiale et 30 secondes pour la durée de la mémoire tampon de lecture en cours.

1. Configurez la variable `BufferControlParameters` qui encapsule les paramètres initiaux de durée de la mémoire tampon et de durée de la lecture :

       Cette classe fournit deux méthodes d’usine :
   
   * Pour définir la durée initiale de la mémoire tampon sur celle de la lecture :

     ```java
     public static BufferControlParameters createSimple( 
         long bufferTime)
     ```

   * Pour définir les heures de mémoire tampon initiales et de lecture :

     ```java
     public static BufferControlParameters createDual( 
         long initialBuffer,   
         long bufferTime)
     ```

     Ces méthodes renvoient une `IllegalArgumentException` si les paramètres ne sont pas valides, par exemple :

   * La durée initiale de la mémoire tampon est inférieure à zéro.
   * Le temps de mémoire tampon initial est supérieur au temps de mémoire tampon.

1. Pour définir les valeurs des paramètres de mémoire tampon, utilisez cette méthode. `MediaPlayer` method :

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. Pour obtenir les valeurs actuelles du paramètre de mémoire tampon, utilisez cette méthode. `MediaPlayer` method :

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

   Si l’AVE ne parvient pas à définir les valeurs spécifiées, le lecteur multimédia entre dans la variable `ERROR` État avec le code d’erreur `SET_BUFFER_PARAMETERS_ERROR`.

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

Par exemple, pour définir la mémoire tampon initiale sur 2 secondes et la durée de la mémoire tampon de lecture sur 30 secondes :

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(2000, 30000));
```

L’implémentation de la référence Primetime illustre cette fonctionnalité. Utilisez les paramètres de l’application pour définir les valeurs de la mémoire tampon.
