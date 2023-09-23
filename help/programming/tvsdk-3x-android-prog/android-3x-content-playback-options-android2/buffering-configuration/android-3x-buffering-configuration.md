---
description: Pour offrir une expérience de visionnage plus fluide, TVSDK place parfois la vidéo en mémoire tampon. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.
title: Mise en mémoire tampon
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# Présentation {#buffering-overview}

Pour offrir une expérience de visionnage plus fluide, TVSDK place parfois la vidéo en mémoire tampon. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.

TVSDK définit une durée de mise en mémoire tampon de lecture d’au moins 30 secondes et une durée de mise en mémoire tampon initiale avant le démarrage de la lecture du média, d’au moins 2 secondes. Après les appels de l’application `play`, mais avant le début de la lecture, TVSDK met le média en mémoire tampon jusqu’à la date initiale pour offrir un démarrage fluide lorsqu’il commence réellement la lecture.

Vous pouvez modifier les temps de mise en mémoire tampon en définissant de nouvelles stratégies de mise en mémoire tampon, et vous pouvez modifier le moment où la mise en mémoire tampon initiale a lieu instantanément.

## Stratégies de mise en mémoire tampon {#section_9B3407D52F1E4CB48E7A4836EBDA8F70}

Selon votre environnement (y compris le périphérique, le système d’exploitation ou les conditions réseau), vous pouvez définir différentes stratégies de mise en mémoire tampon pour votre lecteur, comme la modification de la durée minimale pour la mise en mémoire tampon initiale et la mise en mémoire tampon de la lecture en cours.

Après avoir appelé `play`, le lecteur multimédia commence la mise en mémoire tampon de la vidéo. Lorsque le lecteur multimédia a mis en mémoire tampon la quantité de vidéo indiquée par la date initiale de mise en mémoire tampon, la lecture commence. Ce processus améliore le temps de démarrage, car le lecteur n’attend pas que la totalité de la mémoire tampon de lecture soit remplie avant de démarrer la lecture. Au lieu de cela, après la mise en mémoire tampon des quelques secondes initiales, la lecture commence.

Pendant le rendu de la vidéo, TVSDK continue de mettre en mémoire tampon les nouveaux fragments jusqu’à ce qu’il ait mis en mémoire tampon la quantité spécifiée par le délai de mise en mémoire tampon de la lecture. Si la longueur actuelle de la mémoire tampon tombe en dessous du temps de la mémoire tampon de lecture, le lecteur télécharge des fragments supplémentaires. Une fois que la longueur de la mémoire tampon actuelle est supérieure de quelques secondes à celle de la lecture, TVSDK arrête le téléchargement des fragments.

>[!TIP]
>
>Si la valeur initiale de la mémoire tampon est élevée, cela peut donner à l’utilisateur un temps de mise en mémoire tampon initial long avant de commencer. Cela peut offrir une lecture fluide pendant une période plus longue ; cependant, si les conditions réseau sont mauvaises, la lecture initiale peut être retardée.

Si vous activez l’instantané en appelant `prepareBuffer`, la mise en mémoire tampon initiale commence à ce moment, au lieu d’attendre `play`.

## Définition des heures de mise en mémoire tampon {#section_05CDD927869D47EBA1D2069B1416B2E4}

La variable `MediaPlayer` fournit des méthodes pour définir et obtenir l’heure de mise en mémoire tampon initiale et l’heure de mise en mémoire tampon de la lecture.

>[!TIP]
>
>Si vous ne définissez pas les paramètres de contrôle de la mémoire tampon avant de commencer la lecture, le lecteur multimédia met par défaut 2 secondes pour la mémoire tampon initiale et 30 secondes pour la durée de la mémoire tampon de lecture en cours.

1. Configurez la variable `BufferControlParameters` qui encapsule les paramètres initiaux de durée de la mémoire tampon et de durée de la lecture.

   Cette classe fournit les méthodes d’usine suivantes :

   * Pour définir la durée initiale de la mémoire tampon sur celle de la lecture :

     ```
     public static BufferControlParameters createSimple(long bufferTime)
     ```

   * Pour définir les heures de mémoire tampon initiales et de lecture :

     ```
     public static BufferControlParameters createDual( 
       long initialBuffer,  
       long bufferTime)
     ```

   Si les paramètres ne sont pas valides, ces méthodes renvoient `MediaPlayerException` avec le code d’erreur `PSDKErrorCode.INVALID_ARGUMENT`, par exemple lorsque les conditions suivantes sont remplies :

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

<!--<a id="example_DE0580B3AD404635825D3301C1F096B6"></a>-->

Par exemple, pour définir la mémoire tampon initiale sur 5 secondes et la durée de la mémoire tampon de lecture sur 30 secondes :

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(5000, 30000));
```
