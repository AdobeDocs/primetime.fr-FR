---
description: Pour une visualisation plus fluide, le navigateur TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.
seo-description: Pour une visualisation plus fluide, le navigateur TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.
seo-title: Mise en mémoire tampon
title: Mise en mémoire tampon
uuid: 9937731d-013e-41e9-a4c9-f7a54a5e654d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise en mémoire tampon{#buffering}

Pour une visualisation plus fluide, le navigateur TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.

Le navigateur TVSDK définit une durée de mémoire tampon de lecture d’au moins 30 secondes et une durée de mémoire tampon initiale d’au moins 2 secondes avant le début de lecture du média. Après les appels de l’application `play` mais avant le début de la lecture, le navigateur TVSDK met le média en mémoire tampon jusqu’à la mise en mémoire tampon initiale afin d’offrir un début fluide lorsqu’il début réellement la lecture.

## Définition des heures de mise en mémoire tampon {#section_179DA7CA865D48EBA4B03D50B6B7BC50}

MediaPlayer fournit des méthodes pour définir et obtenir la mise en mémoire tampon initiale et la mise en mémoire tampon de la lecture.

>[!TIP]
>
>Si vous ne définissez pas les paramètres de contrôle de la mémoire tampon avant de commencer la lecture, le lecteur multimédia prend par défaut 2 secondes pour la mémoire tampon initiale et 30 secondes pour la durée de la mémoire tampon de lecture en cours.

* Pour utiliser les paramètres de mémoire tampon, utilisez l’attribut `bufferControlParameters` de MediaPlayer.

   Par exemple, pour définir la mémoire tampon initiale sur 2 secondes et la durée de lecture sur 30 secondes :

   ```js
   var params = new AdobePSDK.BufferControlParameters(2000, 30000);
   ```

## Mise en mémoire tampon des stratégies de temps {#section_7EF2947931654CCC8DAB9172391FA4EB}

En fonction de votre environnement (y compris le périphérique, le système d’exploitation ou les conditions réseau), vous pouvez définir différentes stratégies de mise en mémoire tampon pour votre lecteur, telles que la modification de la durée minimale de mise en mémoire tampon initiale et de mise en mémoire tampon de la lecture en cours.

Une fois que vous avez appelé `play`, le lecteur multimédia commence à mettre la vidéo en mémoire tampon. Lorsque le lecteur multimédia a mis en mémoire tampon la quantité de vidéo spécifiée par le temps de mémoire tampon initial, la lecture commence. Ce processus améliore le début de la lecture, car le lecteur n’attend pas que la totalité de la mémoire tampon de lecture soit remplie avant de commencer la lecture. Au lieu de cela, après la mise en mémoire tampon des quelques secondes initiales, la lecture commence.

Pendant le rendu de la vidéo, le navigateur TVSDK continue à mettre en mémoire tampon les nouveaux fragments jusqu’à ce qu’il ait mis en mémoire tampon la quantité spécifiée par la durée de la mémoire tampon de lecture. Si la longueur actuelle de la mémoire tampon tombe sous la durée de la mémoire tampon de lecture, le lecteur télécharge des fragments supplémentaires. Une fois que la longueur de la mémoire tampon actuelle est supérieure à la durée de la mémoire tampon de lecture de quelques secondes, le navigateur TVSDK arrête de télécharger les fragments.

>[!TIP]
>
>Si la valeur initiale de la mémoire tampon est élevée, cela peut donner à votre utilisateur une longue période de mise en mémoire tampon initiale avant de commencer. Cela peut permettre une lecture en douceur plus longue ; toutefois, si les conditions réseau sont mauvaises, la lecture initiale pourrait être retardée.

