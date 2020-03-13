---
description: Il y a certaines limites et certains problèmes dans le comportement du mode de jeu par les tours.
seo-description: Il y a certaines limites et certains problèmes dans le comportement du mode de jeu par les tours.
seo-title: Limites et comportement pour le jeu par astuces
title: Limites et comportement pour le jeu par astuces
uuid: 0e84c9ef-fc18-4667-ad17-7f4777b552ba
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Limites et comportement pour le jeu par astuces{#limitations-and-behavior-for-trick-play}

Il y a certaines limites et certains problèmes dans le comportement du mode de jeu par les tours.

<!--<a id="section_8B88E281A0FA4661B4C2C70A0ABED57C"></a>-->

Voici les limites du mode de jeu par astuces :

* La liste de lecture principale doit contenir des segments d’image I uniquement. Seules les images clés de la piste I-frame s’affichent à l’écran.
* La piste audio et les sous-titres sont désactivés.
* La logique ABR (Adaptive bit rate) est désactivée. TVSDK sélectionne un débit entre le débit fourni le plus faible et 800 kbit/s et l’utilise pendant toute la session de jeu vidéo.
* La lecture et la mise en pause sont activées.
* La recherche est refusée. Pour effectuer une recherche, appelez `pause` pour quitter le mode de jeu par astuce, puis appelez `seek`.

* Vous pouvez passer du mode de lecture de l’astuce à n’importe quel taux de lecture autorisé (lecture ou pause).
* Lorsque des publicités sont intégrées au flux :

   * Vous pouvez jouer uniquement lors de la lecture du contenu principal. Une erreur est diffusée si vous tentez de basculer vers l’astuce play pendant une coupure publicitaire.
   * Après avoir démarré le mode de lecture par astuce, les coupures publicitaires sont ignorées et aucun publicitaire n’est déclenché.
   * La chronologie exposée par TVSDK à l’application du lecteur n’est pas modifiée, même si les coupures publicitaires sont ignorées.
   * La valeur d’heure actuelle saute vers l’avant (en avant rapide) ou vers l’arrière (en arrière rapide) avec la durée de la coupure publicitaire ignorée. Ce comportement de saut pour l’instant présent permet à la durée du flux de rester inchangée pendant la lecture de l’astuce. Votre application de lecteur peut obtenir la valeur d’heure locale pour effectuer le suivi de l’heure par rapport au contenu principal uniquement. Les sauts de temps ne sont pas effectués sur les valeurs renvoyées pour l’heure locale lors de la saut d’une publicité.
   * Le  `MediaPlayerEvent.AD_BREAK_SKIPPED` est distribué immédiatement avant qu’une coupure publicitaire ne soit sur le point d’être ignorée. Votre lecteur peut utiliser ce pour implémenter la logique personnalisée liée aux coupures publicitaires ignorées.
   * La sortie d’un jeu de astuces appelle la même stratégie de lecture de publicité que lors de la sortie de la recherche.

      Par conséquent, comme dans le cas de la recherche, le comportement dépend de la différence entre la stratégie de lecture de votre application et la stratégie par défaut. La valeur par défaut est que la dernière coupure publicitaire ignorée est lue au point où vous sortez du mode de lecture par astuce.

