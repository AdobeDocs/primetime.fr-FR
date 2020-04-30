---
description: Pour une visualisation plus fluide, TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.
seo-description: Pour une visualisation plus fluide, TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.
seo-title: Mise en mémoire tampon des stratégies de temps
title: Mise en mémoire tampon des stratégies de temps
uuid: 8d3ce9be-cca4-485e-ba66-d2f2aa6822dd
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Mise en mémoire tampon des stratégies de temps {#buffering-time-policies}

Pour une visualisation plus fluide, TVSDK met parfois en mémoire tampon le flux vidéo. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.

TVSDK définit une durée de mémoire tampon de lecture d’au moins 30 secondes et une durée initiale de mémoire tampon d’au moins 5 secondes avant le début de lecture du média. Après les appels de l’application `play` mais avant le début de la lecture, TVSDK met le média en mémoire tampon jusqu’à la mise en mémoire tampon initiale afin d’offrir un début fluide lorsqu’il début effectivement la lecture.

Vous pouvez modifier les temps de mise en mémoire tampon en définissant de nouvelles stratégies de mise en mémoire tampon.

<!--<a id="section_F6EEE15600814A70A57CCBACE20D68BD"></a>-->

En fonction de votre environnement (y compris le périphérique, le système d’exploitation ou les conditions réseau), vous pouvez définir différentes stratégies de mise en mémoire tampon pour votre lecteur, telles que la modification de la durée minimale de mise en mémoire tampon initiale et de mise en mémoire tampon de la lecture en cours.

Une fois que vous avez appelé `play`, le lecteur multimédia commence à mettre la vidéo en mémoire tampon. Lorsque le lecteur multimédia a mis en mémoire tampon la quantité de vidéo spécifiée par le temps de mémoire tampon initial, la lecture commence. Ce processus améliore le début de la lecture, car le lecteur n’attend pas que la totalité de la mémoire tampon de lecture soit remplie avant de commencer la lecture. Au lieu de cela, après la mise en mémoire tampon des quelques secondes initiales, la lecture commence.

Pendant le rendu de la vidéo, TVSDK continue à mettre en mémoire tampon les nouveaux fragments jusqu’à ce qu’il ait mis en mémoire tampon la quantité spécifiée par la durée de la mémoire tampon de lecture. Si la longueur actuelle de la mémoire tampon tombe sous la durée de la mémoire tampon de lecture, le lecteur télécharge des fragments supplémentaires. Une fois que la longueur de la mémoire tampon actuelle est supérieure à la durée de la mémoire tampon de lecture de quelques secondes, TVSDK arrête de télécharger les fragments.

>[!TIP]
>
>Si la valeur initiale de la mémoire tampon est élevée, cela peut donner à votre utilisateur une longue période de mise en mémoire tampon initiale avant de commencer. Cela peut permettre une lecture en douceur plus longue ; toutefois, si les conditions réseau sont mauvaises, la lecture initiale pourrait être retardée.

