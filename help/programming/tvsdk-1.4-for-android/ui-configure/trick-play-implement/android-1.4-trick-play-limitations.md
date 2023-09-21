---
description: Il existe certaines limites et certains problèmes dans le comportement du mode de lecture des astuces.
title: Limites et comportement pour la lecture de l’astuce
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Limites et comportement pour la lecture de l’astuce{#limitations-and-behavior-for-trick-play}

Il existe certaines limites et certains problèmes dans le comportement du mode de lecture des astuces.

<!--<a id="section_8B88E281A0FA4661B4C2C70A0ABED57C"></a>-->

Voici les limites du mode de lecture des astuces :

* La liste de lecture principale doit contenir des segments d’image I uniquement. Seules les images clés de la piste d’i-frame s’affichent à l’écran.
* La piste audio et les sous-titres fermés sont désactivés.
* La logique de débit adaptatif (ABR) est désactivée. TVSDK sélectionne un débit entre le débit fourni le plus faible et 800 Kbit/s et l’utilise pendant toute la session de lecture de l’astuce.
* La lecture et la pause sont activées.
* La recherche est refusée. Pour rechercher, appelez `pause` pour quitter le mode de lecture de l’astuce, puis appelez `seek`.

* Vous pouvez passer du mode de lecture des astuces à n’importe quel taux de lecture autorisé (lecture ou pause).
* Lorsque des publicités sont intégrées dans la diffusion :

   * Vous pouvez jouer uniquement lors de la lecture du contenu principal. Une erreur est envoyée si vous essayez de basculer vers l’astuce lors d’une coupure publicitaire.
   * Après avoir commencé le mode de lecture des astuces, les coupures publicitaires sont ignorées et aucun événement publicitaire n’est déclenché.
   * La chronologie exposée par TVSDK à l’application du lecteur n’est pas modifiée même si des coupures publicitaires sont ignorées.
   * La valeur d’heure actuelle est un saut en avant (à l’avance rapide) ou en arrière (à l’arrière rapide) avec la durée de la coupure publicitaire ignorée. Ce comportement de saut pour l’heure actuelle permet à la durée du flux de rester inchangée pendant la lecture de l’astuce. Votre application de lecteur peut obtenir la valeur de l’heure locale pour effectuer le suivi de la durée par rapport au contenu principal uniquement. Aucun saut de temps n’est effectué sur les valeurs renvoyées pour l’heure locale lors de la saut d’une publicité.
   * La variable `MediaPlayerEvent.AD_BREAK_SKIPPED` est distribué immédiatement avant qu’une coupure publicitaire ne soit sur le point d’être ignorée. Votre lecteur peut utiliser cet événement pour implémenter la logique personnalisée liée aux coupures publicitaires ignorées.
   * La sortie d’un jeu de astuces appelle la même stratégie de lecture de publicité que lorsque vous quittez la recherche.

     Par conséquent, comme pour la recherche, le comportement dépend de la différence entre la stratégie de lecture de votre application et la stratégie par défaut. La valeur par défaut est que la dernière coupure publicitaire ignorée est lue au point où vous sortez du mode de lecture de l’astuce.
