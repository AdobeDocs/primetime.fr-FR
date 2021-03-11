---
description: Il y a certaines limites et certains problèmes dans le comportement du mode de jeu de l'astuce.
title: Limites et comportement pour le jeu par astuces
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# Limites et comportement pour le jeu vidéo{#limitations-and-behavior-for-trick-play}

Il y a certaines limites et certains problèmes dans le comportement du mode de jeu de l&#39;astuce.

<!--<a id="section_8B88E281A0FA4661B4C2C70A0ABED57C"></a>-->

Voici les limites du mode de lecture des astuces :

* La liste de lecture principale doit contenir des segments d’image I uniquement. Seules les images clés de la piste I-frame s’affichent à l’écran.
* La piste audio et les légendes fermées sont désactivées.
* La logique ABR (Adaptive Bbit Rate) est désactivée. TVSDK sélectionne un débit entre le débit fourni le plus faible et 800 kbit/s et l’utilise pendant toute la session de lecture.
* La lecture et la mise en pause sont activées.
* La recherche est interdite. Pour effectuer une recherche, appelez `pause` pour quitter le mode de lecture de l&#39;astuce, puis appelez `seek`.

* Vous pouvez passer du mode de lecture des astuces à n’importe quel taux de lecture autorisé (lecture ou pause).
* Lorsque des publicités sont incorporées dans le flux :

   * Vous pouvez jouer uniquement lors de la lecture du contenu principal. Une erreur est diffusée si vous tentez de basculer vers l’astuce au cours d’une coupure publicitaire.
   * Après avoir commencé le mode de lecture des astuces, les coupures publicitaires sont ignorées et aucun événement publicitaire n’est déclenché.
   * La chronologie exposée par TVSDK à l’application du lecteur n’est pas modifiée même si des coupures publicitaires sont ignorées.
   * La valeur d’heure actuelle saute vers l’avant (en avant rapide) ou vers l’arrière (en arrière rapide) avec la durée de la coupure publicitaire ignorée. Ce comportement de saut pour l’heure actuelle permet à la durée du flux de rester inchangée pendant la lecture de l’astuce. Votre application de lecteur peut obtenir la valeur d’heure locale pour effectuer le suivi de l’heure par rapport au contenu principal uniquement. Les sauts de temps ne sont pas effectués sur les valeurs renvoyées pour l’heure locale lors de l’abandon d’une publicité.
   * Le événement `MediaPlayerEvent.AD_BREAK_SKIPPED` est distribué immédiatement avant qu’une coupure publicitaire ne soit sur le point d’être ignorée. Votre lecteur peut utiliser ce événement pour implémenter une logique personnalisée liée aux coupures publicitaires ignorées.
   * La sortie d’un jeu vidéo appelle la même stratégie de lecture publicitaire que lors de la sortie de la recherche.

      Par conséquent, comme dans le cas de la recherche, le comportement dépend de la différence entre la stratégie de lecture de l’application et la stratégie par défaut. La valeur par défaut est que la dernière coupure publicitaire sautée est lue au point où vous sortez du mode de lecture par astuces.

