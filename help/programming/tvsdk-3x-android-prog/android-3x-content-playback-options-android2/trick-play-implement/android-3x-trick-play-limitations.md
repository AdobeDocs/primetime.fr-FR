---
description: 'null'
seo-description: 'null'
seo-title: Limites et comportement pour le jeu par astuces
title: Limites et comportement pour le jeu par astuces
uuid: c28cc8db-3f45-488e-ab72-b102b3a1fab2
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Limites et comportement pour le jeu par astuces {#limitations-and-behavior-for-trick-play}

<!--<a id="section_2BC43539C5C142E085D06A7E35C76726"></a>-->

Limites du mode de jeu par astuce :

* La liste de lecture principale doit contenir des segments Iframe uniquement.

   Seules les images clés de la piste Iframe s’affichent à l’écran.
* La piste audio et les sous-titres sont désactivés.
* La lecture et la mise en pause sont activées.
* Vous pouvez quitter le mode de lecture par astuce dans n’importe quel taux de lecture autorisé (lecture ou pause).
* Lorsque des publicités sont intégrées au flux :

   * Vous pouvez jouer uniquement lors de la lecture du contenu principal. Une erreur est diffusée si vous tentez de basculer vers l’astuce play pendant une coupure publicitaire.
   * Après le démarrage du mode de lecture par astuce, les coupures publicitaires sont ignorées et aucun publicitaire n’est déclenché.
   * La chronologie exposée par TVSDK au lecteur n’est pas modifiée, même si les coupures publicitaires sont ignorées.
   * La valeur d’heure actuelle saute vers l’avant (en avant rapide) ou vers l’arrière (en arrière rapide) avec la durée de la coupure publicitaire ignorée.

      Ce comportement de saut pour l’instant présent permet à la durée du flux de rester inchangée pendant la lecture de l’astuce. Votre lecteur peut suivre le temps relatif uniquement au contenu principal. Les sauts de temps ne sont pas effectués sur les valeurs renvoyées pour l’heure locale lors de la saut d’une publicité.
   * Le  `MediaPlayerEvent.AD_BREAK_SKIPPED` est distribué immédiatement avant qu’une coupure publicitaire ne soit sur le point d’être ignorée.

      Votre lecteur peut utiliser ce pour implémenter la logique personnalisée liée aux coupures publicitaires ignorées.

   * La sortie d’un jeu de astuces appelle la même stratégie de lecture de publicité que lors de la sortie de la recherche.

      Comme pour la recherche, le comportement dépend de la différence entre la stratégie de lecture de votre application et la stratégie par défaut. La valeur par défaut est que la dernière coupure publicitaire sautée est lue au point où vous sortez de la lecture de l’astuce.