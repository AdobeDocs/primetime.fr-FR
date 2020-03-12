---
description: Pour une visualisation plus fluide, TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la mise en mémoire tampon du lecteur.
seo-description: Pour une visualisation plus fluide, TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la mise en mémoire tampon du lecteur.
seo-title: Mise en mémoire tampon
title: Mise en mémoire tampon
uuid: 7f9f0deb-5f18-441d-b7a4-67c631a798f4
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Présentation {#buffering-overview}

Pour une visualisation plus fluide, TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la mise en mémoire tampon du lecteur.

TVSDK définit une durée de mémoire tampon de lecture d’au moins 30 secondes et une durée initiale de mémoire tampon d’au moins 2 secondes avant la lecture du multimédia. Après les appels de l’application `play`, mais avant le début de la lecture, TVSDK met le média en mémoire tampon jusqu’à la durée initiale afin de donner un  fluide lorsqu’il est en fait en train de .

Vous pouvez modifier les temps de mise en mémoire tampon en définissant de nouvelles stratégies de mise en mémoire tampon et vous pouvez modifier le moment où la mise en mémoire tampon initiale a lieu en utilisant l’option d’activation instantanée.

## Mise en mémoire tampon des stratégies de temps {#section_9B3407D52F1E4CB48E7A4836EBDA8F70}

En fonction de votre  de  (y compris le périphérique, le système d’exploitation ou les conditions réseau), vous pouvez définir différentes stratégies de mise en mémoire tampon pour votre lecteur, telles que la modification de la durée minimale de mise en mémoire tampon initiale et de mise en mémoire tampon de la lecture en cours.

Une fois que vous avez appelé `play`, le lecteur multimédia commence à mettre la vidéo en mémoire tampon. Lorsque le lecteur multimédia a mis en mémoire tampon la quantité de vidéo spécifiée par le temps de mise en mémoire tampon initial, la lecture commence. Ce processus améliore le temps de  du lecteur, car celui-ci n’attend pas que la totalité du tampon de lecture soit remplie avant de commencer la lecture. Au lieu de cela, après quelques secondes initiales mises en mémoire tampon, la lecture commence.

Pendant le rendu de la vidéo, TVSDK continue à mettre en mémoire tampon les nouveaux fragments jusqu’à ce qu’il ait mis en mémoire tampon la quantité spécifiée par la durée de la mémoire tampon de lecture. Si la longueur actuelle de la mémoire tampon tombe sous la durée de la mémoire tampon de lecture, le lecteur télécharge des fragments supplémentaires. Une fois que la longueur actuelle de la mémoire tampon est supérieure à la durée de la mémoire tampon de lecture de quelques secondes, TVSDK arrête le téléchargement des fragments.

>[!TIP]
>
>Si la valeur initiale de la mémoire tampon est élevée, cela peut donner à votre utilisateur une longue période de mise en mémoire tampon initiale avant de commencer. Cela peut permettre une lecture en douceur pendant une durée plus longue ; toutefois, si les conditions réseau sont mauvaises, la lecture initiale peut être retardée.

Si vous activez instantanément en appelant `prepareBuffer`, la mise en mémoire tampon initiale commence à ce moment, au lieu d’attendre `play`.

## Définition des heures de mise en mémoire tampon {#section_05CDD927869D47EBA1D2069B1416B2E4}

Le `MediaPlayer` fournit des méthodes pour définir et obtenir le temps de mise en mémoire tampon initiale et le temps de mise en mémoire tampon de la lecture.

>[!TIP]
>
>Si vous ne définissez pas les paramètres de contrôle de la mémoire tampon avant de commencer la lecture, le lecteur multimédia prend par défaut la valeur 2 secondes pour la mémoire tampon initiale et 30 secondes pour la durée de la mémoire tampon de lecture en cours.

1. Configurez l’ `BufferControlParameters` objet, qui encapsule les paramètres initiaux de temps de mémoire tampon et de temps de mémoire tampon de lecture.

   Cette classe fournit les méthodes de fabrique suivantes :

   * Pour définir la durée initiale de la mémoire tampon sur la durée de la lecture :

      ```
      public static BufferControlParameters createSimple(long bufferTime)
      ```

   * Pour définir les heures de mémoire tampon initiale et de lecture :

      ```
      public static BufferControlParameters createDual( 
        long initialBuffer,  
        long bufferTime)
      ```
   Si les paramètres ne sont pas valides, ces méthodes renvoient `MediaPlayerException` le code d’erreur `PSDKErrorCode.INVALID_ARGUMENT`, par exemple lorsque les conditions suivantes sont remplies :

   * La durée initiale du tampon est inférieure à zéro.
   * La durée initiale de la mémoire tampon est supérieure à la durée de la mémoire tampon.


1. Pour définir les valeurs des paramètres de mémoire tampon, utilisez cette `MediaPlayer` méthode :

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. Pour obtenir les valeurs actuelles des paramètres de mémoire tampon, utilisez cette `MediaPlayer` méthode :

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

<!--<a id="example_DE0580B3AD404635825D3301C1F096B6"></a>-->

Par exemple, pour définir la mémoire tampon initiale sur 5 secondes et la durée de la mémoire tampon de lecture sur 30 secondes :

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(5000, 30000));
```
