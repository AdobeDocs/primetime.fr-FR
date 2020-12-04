---
description: 'null'
seo-description: 'null'
seo-title: Limites et comportement pour le jeu par astuces
title: Limites et comportement pour le jeu par astuces
uuid: c28cc8db-3f45-488e-ab72-b102b3a1fab2
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# Limites et comportement pour le jeu vidéo {#limitations-and-behavior-for-trick-play}

<!--<a id="section_2BC43539C5C142E085D06A7E35C76726"></a>-->

Limites du mode de lecture des astuces :

* La liste de lecture principale doit contenir des segments Iframe uniquement.

   Seules les images clés de la piste Iframe s’affichent à l’écran.
* La piste audio et les légendes fermées sont désactivées.
* La lecture et la mise en pause sont activées.
* Vous pouvez quitter le mode de lecture par astuces pour n’importe quel taux de lecture autorisé (lecture ou pause).
* Lorsque des publicités sont incorporées dans le flux :

   * Vous pouvez jouer uniquement lors de la lecture du contenu principal. Une erreur est diffusée si vous tentez de basculer vers l’astuce au cours d’une coupure publicitaire.
   * Après avoir démarré le mode de lecture des astuces, les coupures publicitaires sont ignorées et aucun événement publicitaire n’est déclenché.
   * La chronologie exposée par TVSDK au lecteur n’est pas modifiée même si des coupures publicitaires sont ignorées.
   * La valeur d’heure actuelle saute vers l’avant (en avant rapide) ou vers l’arrière (en arrière rapide) avec la durée de la coupure publicitaire ignorée.

      Ce comportement de saut pour l’heure actuelle permet à la durée du flux de rester inchangée pendant la lecture de l’astuce. Votre lecteur peut suivre l’heure par rapport au contenu principal uniquement. Les sauts de temps ne sont pas effectués sur les valeurs renvoyées pour l’heure locale lors de l’abandon d’une publicité.
   * Le événement `MediaPlayerEvent.AD_BREAK_SKIPPED` est distribué immédiatement avant qu’une coupure publicitaire ne soit sur le point d’être ignorée.

      Votre lecteur peut utiliser ce événement pour implémenter une logique personnalisée liée aux coupures publicitaires ignorées.

   * La sortie d’un jeu vidéo appelle la même stratégie de lecture publicitaire que lors de la sortie de la recherche.

      Comme pour la recherche, le comportement dépend de la différence entre la stratégie de lecture de l’application et la stratégie par défaut. La valeur par défaut est que la dernière coupure publicitaire sautée est lue à l’endroit où vous sortez de la lecture de l’astuce.