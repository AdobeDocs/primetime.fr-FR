---
description: Pour offrir une expérience de visionnage plus fluide, TVSDK place parfois la vidéo en mémoire tampon. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.
title: Stratégies de mise en mémoire tampon
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Stratégies de mise en mémoire tampon {#buffering-time-policies}

Pour offrir une expérience de visionnage plus fluide, TVSDK place parfois la vidéo en mémoire tampon. Vous pouvez configurer la manière dont le lecteur met en mémoire tampon.

TVSDK définit une durée de mémoire tampon de lecture d’au moins 30 secondes et une durée de mémoire tampon initiale d’au moins 5 secondes avant le début de la lecture du média. Après les appels de l’application `play` mais avant le début de la lecture, TVSDK met le média en mémoire tampon jusqu’à la date initiale pour offrir un démarrage fluide lorsqu’il commence réellement la lecture.

Vous pouvez modifier les temps de mise en mémoire tampon en définissant de nouvelles stratégies de mise en mémoire tampon.

<!--<a id="section_F6EEE15600814A70A57CCBACE20D68BD"></a>-->

Selon votre environnement (y compris le périphérique, le système d’exploitation ou les conditions réseau), vous pouvez définir différentes stratégies de mise en mémoire tampon pour votre lecteur, comme la modification de la durée minimale pour la mise en mémoire tampon initiale et la mise en mémoire tampon de la lecture en cours.

Après avoir appelé `play`, le lecteur multimédia commence la mise en mémoire tampon de la vidéo. Lorsque le lecteur multimédia a mis en mémoire tampon la quantité de vidéo indiquée par la date initiale de mise en mémoire tampon, la lecture commence. Ce processus améliore le temps de démarrage, car le lecteur n’attend pas que la totalité de la mémoire tampon de lecture soit remplie avant de démarrer la lecture. Au lieu de cela, après la mise en mémoire tampon des quelques secondes initiales, la lecture commence.

Pendant le rendu de la vidéo, TVSDK continue de mettre en mémoire tampon les nouveaux fragments jusqu’à ce qu’il ait mis en mémoire tampon la quantité spécifiée par le délai de mise en mémoire tampon de la lecture. Si la longueur actuelle de la mémoire tampon tombe en dessous du temps de la mémoire tampon de lecture, le lecteur télécharge des fragments supplémentaires. Une fois que la longueur de la mémoire tampon actuelle est supérieure de quelques secondes à celle de la lecture, TVSDK arrête le téléchargement des fragments.

>[!TIP]
>
>Si la valeur initiale de la mémoire tampon est élevée, cela peut donner à l’utilisateur un temps de mise en mémoire tampon initial long avant de commencer. Cela peut offrir une lecture fluide pendant une période plus longue ; cependant, si les conditions réseau sont mauvaises, la lecture initiale peut être retardée.
